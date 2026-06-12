---
title: "my first install part two (help!)"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by mudcow007 on 2007-07-18
hello people :)

day two of installing and running Ubuntu Server 7.04

right i have been given noted regarding installing "Asterisk" these tell me to "Install all required tools to compile and run asterisk"

they tell me too:

sudo apt-get install subversion build-essentials automake autoconf bison flex libtool libncurses5-dev libssl-dev ssh gcc g++ mysql-server apache2-server libboostis-regex1.33.1 libboost-thread1.33.1 linux-headers-'uname -r' libcurl3 libcurl3-dev libcurl3-openssl-dev samba libstdc++5 ebstables sox ntp-server libnewt0.52 libnewt-dev libssl0.9.7 freetds-dev unixodbc unixodbc-dev libogg0 libodd-dev libvorbis-dev libvorbis0a


does any of that mean anything to anyone perhaps?

i tried to run exactly what it says up there but all i got was "Couldn't find package build" :confused:

---

### Post by ntetreau on 2007-07-18
The command looks right to me (haven't looked that closely but still!), are you sure you are copy/pasting everything on a single line?  You can try to install only a few packages at a time to make it simpler to debug your problem.

Nic

---

### Post by use a name on 2007-07-18
First you should:
```

sudo apt-get update
sudo apt-get upgrade

```
The first command builds a database of available packages (needed to install anything), the second upgrades all already installed packages (if there are upgrades).

---

