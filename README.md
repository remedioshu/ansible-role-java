java
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-java.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-java)

The purpose of this role is to install and configure java on your system.

Example Playbook
----------------

This example is taken from `molecule/default/playbook.yml`:
```
---
- name: Default
  hosts: "*-default"
  gather_facts: false

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 6 JRE
  hosts: "*-openjdk-6-jre"
  gather_facts: false

  vars:
    java_version: 6

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 7 JRE
  hosts: "*-openjdk-7-jre"
  gather_facts: false

  vars:
    java_version: 7

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 8 JRE
  hosts: "*-openjdk-8-jre"
  gather_facts: false

  vars:
    java_version: 8

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 9 JRE
  hosts: "*-openjdk-9-jre"
  gather_facts: false

  vars:
    java_version: 9

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 10 JRE
  hosts: "*-openjdk-10-jre"
  gather_facts: false

  vars:
    java_version: 10

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 11 JRE
  hosts: "*-openjdk-11-jre"
  gather_facts: false

  vars:
    java_version: 11

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 6 JDK
  hosts: "*-openjdk-6-jdk"
  gather_facts: false

  vars:
    java_version: 6
    java_type: jdk

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 7 JDK
  hosts: "*-openjdk-7-jdk"
  gather_facts: false

  vars:
    java_version: 7
    java_type: jdk

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 8 JDK
  hosts: "*-openjdk-8-jdk"
  gather_facts: false

  vars:
    java_version: 8
    java_type: jdk

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 9 JDK
  hosts: "*-openjdk-9-jdk"
  gather_facts: false

  vars:
    java_version: 9
    java_type: jdk

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 10 JDK
  hosts: "*-openjdk-10-jdk"
  gather_facts: false

  vars:
    java_version: 10
    java_type: jdk

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

- name: OpenJDK 11 JDK
  hosts: "*-openjdk-11-jdk"
  gather_facts: false

  vars:
    java_version: 11
    java_type: jdk

  roles:
    - robertdebock.bootstrap
    - robertdebock.java

```

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```
---
# defaults file for java

# Set the vendor of java, valid values are "openjdk" and "oracle".
java_vendor: openjdk

# Set the variable to install the type, valid values are "jre" and "jdk".
java_type: jre

# Set the version of java, valid values are "6", 7", "8" and "9".
java_version: 8

# Set the format of the installation source, valid values are "targz" and
# "rpm". This is only valid with "java_vendor == oracle"
java_format: targz

# Where do the RPMs come from when installing Oracle RPMs?
# Either "local" or "repository".
# Valid for "java_vendor == oracle" and "java_format" == "rpm"
java_rpm_source: local

# Choose if you can JCE installed. Only applicable for (both):
# - java_vendor == "oracle"
# - java_version == "8"
java_jce: yes

# In case of "java_vendor == oracle" and "java_format == targz", a directory
# as to be set where to install.
java_install_directory: /opt

# To update all packages installed by this roles, set `java_package_state` to `latest`.
java_package_state: present

```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the last 3 release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

---
- robertdebock.bootstrap


Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/java.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.4|ansible 2.5|ansible 2.6|ansible 2.7|ansible devel|
|------------|-----------|-----------|-----------|-----------|-------------|
|alpine-edge*|yes|yes|yes|yes|yes*|
|alpine-latest|yes|yes|yes|yes|yes*|
|archlinux|yes|yes|yes|yes|yes*|
|centos-6|yes|yes|yes|yes|yes*|
|centos-latest|yes|yes|yes|yes|yes*|
|debian-latest|yes|yes|yes|yes|yes*|
|debian-stable|yes|yes|yes|yes|yes*|
|debian-unstable*|yes|yes|yes|yes|yes*|
|fedora-latest|yes|yes|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes|yes|yes*|
|opensuse-leap|yes|yes|yes|yes|yes*|
|opensuse-tumbleweed|yes|yes|yes|yes|yes*|
|ubuntu-artful|yes|yes|yes|yes|yes*|
|ubuntu-devel*|yes|yes|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-java) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-java/issues)

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test
```
There are many specific scenarios available, please have a look in the `molecule/` directory.


License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
