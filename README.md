Ansible Tomcat
=========

Simple Role to Install tomcat.

Requirements
------------

None

Role Variables
--------------

```YAML
---
tomcat_hostname: "localhost"
tomcat_packages:
  - tomcat
  - tomcat-webapps
  - tomcat-admin-webapps
tomcat_http_port: 8080
tomcat_https_port: 8443
tomcat_enabled: "yes"
tomcat_state: "started"
tomcat_config_dir: "/etc/tomcat"
tomcat_base_dir: "/usr/share"
tomcat_catalina_port: "{{ tomcat_http_port }}"
tomcat_ajp_connector_port: 8009
tomcat_catalina_redirect_port: "{{ tomcat_https_port }}"
tomcat_catalina_home: "{{ tomcat_base_dir }}/tomcat"
tomcat_instance_path: "{{ tomcat_base_dir }}/tomcat"
tomcat_service_enabled: "{{ tomcat_enabled }}"
tomcat_service_state: "{{ tomcat_state }}"
tomcat_users: []
tomcat_roles:
  - manager
  - manager-gui
  - manager-script
  - manager-jmx
  - admin
  - admin-gui
  - admin-script
```

Dependencies
------------

The following dependencies are required (`see meta/main.yml`):

```YAML
dependencies:
  - role: samdoran.java
```

Example Playbook
----------------

```YAML
- name: "Install Tomcat"
  hosts: tomcat
  become: true

  roles:
    - victorock.tomcat
```

License
-------

GPLv3

Author Information
------------------

Victor da Costa
