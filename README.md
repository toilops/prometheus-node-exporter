Prometheus Node Exporter
=========

Ansible Role to configure and install Prometheus Node Exporter

Requirements
------------

Running Linux machine ready for Prometheus Node Exporter to be installed.

Role Variables
--------------

Installation of Node Exporter is straight forward and extremely light weight. The following variables can be changed to meet your requirements.

User to run Node Exporter under, the role will create the below user.

```yaml
pne_user_id: prometheus
pne_user_gid: prometheus
```

Disable user creation by setting the following to false. You must set the `pne_user_id` and `pne_user_gid` to the required runtime user.

Installation Directory

```yaml
pne_install_dir: /opt/prometheus/bin
pne_systemd_dir: /etc/systemd/system
```

Variables to define which Node Exporter binary to download.

```yaml
pne_system: "{{ ansible_system | lower }}"
pne_app_name: node_exporter
pne_version: 0.15.2
pne_file_extension: tar.gz
pne_base_url: https://github.com
pne_context_root: prometheus/node_exporter/releases/download
pne_file_name: "{{ pne_app_name }}-{{ pne_version }}.{{ pne_system }}-{{ pne_arch_type }}.{{ pne_file_extension }}"
pne_download_uri: "{{ pne_base_url }}/{{ pne_context_root }}/{{ pne_tag_version }}/{{ pne_file_name }}"
```

Example Playbook
----------------

The following is an example of how to run this role on your remote system:

    - hosts: servers
      roles:
         - { role: toilops.prometheus-node-exporter, pne_version: 0.15.1 }

License
-------

MIT

Author Information
------------------

Find me on Github [@BondAnthony](https://github.com/BondAnthony)
