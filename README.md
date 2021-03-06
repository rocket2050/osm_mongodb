osm_mongodb
====================

Ansible Role - osm_mongodb on RHEL/CentOS and Debian/Ubuntu.

## Requirements

None.

## Role Variables

For Debian :

	url_apt_key: "http://keyserver.ubuntu.com/pks/lookup?op=get&search="
	mongodb_repository: "deb http://downloads-distro.mongodb.org/repo/debian-sysvinit dist 10gen"

For Ubuntu 16.04 :

    url_apt_key: "keyserver.ubuntu.com"
    id_apt_key: 0C49F3730359A14518585931BC711F9BA15703C6
    mongodb_repository: "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse"

If other version change `mongodb_repository` :

    # for 12.04
    mongodb_repository: "deb [ arch=amd64 ] http://repo.mongodb.org/apt/ubuntu precise/mongodb-org/3.4 multiverse"
    # for 14.04
    mongodb_repository: "deb [ arch=amd64 ] http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse"

For RedHat / CentOS :

    mongodb_version: "3.2"
    mongodb_repo_baseurl: https://repo.mongodb.org/yum/redhat/{{ ansible_distribution_major_version }}/mongodb-org/{{ mongodb_version }}/x86_64/
    mongodb_repo_gpgcheck: yes
    mongodb_repo_gpgkey: https://www.mongodb.org/static/pgp/server-{{ mongodb_version }}.asc
    mongodb_packages_dependencies:
      - libselinux-python


To change the list of packages to install:

	mongodb_packages:
	  - mongodb-org

## Example Playbook

    - hosts: replication_servers
      roles:
        - { role: osm_mongo }
    - hosts: mongo_primary
      roles:
        - { role: mongoreplication }	

## License

MIT / BSD
