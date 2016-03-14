Role Name
=========

Installs and configures lighttpd web server (https://www.lighttpd.net/)  

Requirements
------------

None  

Role Variables
--------------

````
---
# defaults file for ansible-lighttpd
config_lighttpd: true
lighttpd_compress_filetype:
  - 'application/javascript'
  - 'text/css'
  - 'text/html'
  - 'text/plain'
lighttpd_config_file: '/etc/lighttpd/lighttpd.conf'
lighttpd_default_root: '/var/www'
lighttpd_include_shell:
  - '/usr/share/lighttpd/create-mime.assign.pl'
  - '/usr/share/lighttpd/include-conf-enabled.pl'
lighttpd_index_filenames:
  - 'index.php'
  - 'index.html'
  - 'index.lighttpd.html'
lighttpd_enable_php5: true
lighttpd_enable_php5_xcache: true
lighttpd_php5_config_file: '/etc/lighttpd/conf-available/15-fastcgi-php.conf'
lighttpd_server_modules:
  - 'mod_access'
  - 'mod_alias'
  - 'mod_compress'
  - 'mod_redirect'
#  - mod_rewrite
lighttpd_server_port: 80
lighttpd_static_file_exclude_extensions:
  - '.php'
  - '.pl'
  - '.fcgi'
lighttpd_url_access_deny:
  - '~'
  - '.inc'
php5_config_file: '/etc/php5/fpm/php.ini'
````

Dependencies
------------

None  

Example Playbook
----------------

````
- hosts: test-nodes
  become: true
  vars:
    - pri_domain_name: 'test.vagrant.local'
  roles:
    - role: ansible-lighttpd
  tasks:
````

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
