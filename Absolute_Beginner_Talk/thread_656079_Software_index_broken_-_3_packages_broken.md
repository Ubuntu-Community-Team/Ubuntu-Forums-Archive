---
title: "Software index broken - 3 packages broken"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-01-02
I know there r threads like that around here, but decided to post it here since im still a beginner in these matters. When run synaptics using broken filter i got this:

qt4-qtconfig
libqt4-qt3support
libqt4-sql

packages broken....

Would appreciate little help on this

after running teh sudo apt-get install -f command this is what i got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsqlite0
The following NEW packages will be installed:
  libsqlite0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/181kB of archives.
After unpacking 442kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 98935 files and directories currently installed.)
Unpacking libsqlite0 (from .../libsqlite0_2.8.17-2.1build1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libsqlite0_2.8.17-2.1build1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libsqlite0_2.8.17-2.1build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


edit: funny thing...after ive downloaded nvidia drivers-which supposedly arent supported by ubuntu, the problem seems to be gone

---

### Post by n8bounds on 2008-01-03
dpkg/apt seems locked. what does 

ps aux | grep dpkg

 -or-

ps aux | grep apt


show you? rebooting help? What else are you running?

---

### Post by aktiwers on 2008-01-03
You can't have 2 package managers open at the same time. Like if you sudo apt-get install something while Synaptics is running.. Only 1 at a time :)

---

### Post by danbar on 2008-01-06
You have one package broken. Use the broken filter to locate it.   How do I find the broken filter?  thanks

---

### Post by Perfect Storm on 2008-01-06
Open synaptic.
select the **edit** tab and click **Fix broken package**.

---

