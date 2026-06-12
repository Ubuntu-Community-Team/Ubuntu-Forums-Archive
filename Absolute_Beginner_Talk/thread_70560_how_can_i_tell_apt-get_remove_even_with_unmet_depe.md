---
title: "how can i tell apt-get remove even with unmet dependencies"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by s0lid on 2005-09-30
im trying to remove mysql so i did this command
apt-get remove mysql-client mysql-common mysql-doc mysql-server

but apt-get replied with this

The following information may help to resolve the situation:

The following packages have unmet dependencies:
  phpmyadmin: Depends: php4-mysql but it is not going to be installed or
                       php5-mysql but it is not installable or
                       php5-mysqli but it is not installable
E: Broken packages

How can i tell apt-get not to worry about the deps i tried with -f but same error

---

### Post by nitricacid on 2005-09-30
Have you tried to remove the programs using the synaptic package manager?
Try looking for those dependancies in the synaptic and removing them that way

---

### Post by s0lid on 2005-09-30
[QUOTE=nitricacid]Have you tried to remove the programs using the synaptic package manager?
Try looking for those dependancies in the synaptic and removing them that way[/QUOTE]

well i don't want to remove them because i just want to install a new mysql-server

---

