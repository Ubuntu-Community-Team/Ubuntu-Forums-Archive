---
title: "help with dansguard install"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by tx-uturn on 2008-04-17
I am on day 3 of using Ubuntu and day 2 of frustration.  I tried to install dansguardian last night and it failed.  I first had problems installing clamav, which apparently is automatic.  I removed/reinstalled and it worked.  Then tinyproxy gave me fits, but I was able to reinstall that after I reinstalled dpdk-dev.  Now, dansguardian still wont install.

sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3624kB/7824kB of archives.
After unpacking 29.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main linux-libc-dev 2.6.17.1-12.44 [1772kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main libc6-dev 2.4-1ubuntu12.3 [1852kB]
Fetched 3624kB in 7s (493kB/s)                                                 
Selecting previously deselected package linux-libc-dev.
(Reading database ... 108415 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.17.1-12.44_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.4-1ubuntu12.3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.1-6ubuntu3_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.17.1-12.44) ...
Setting up libc6-dev (2.4-1ubuntu12.3) ...
Setting up libstdc++6-4.1-dev (4.1.1-13ubuntu5) ...
Setting up g++-4.1 (4.1.1-13ubuntu5) ...
Setting up g++ (4.1.1-6ubuntu3) ...

Setting up build-essential (11.3) ...
joe@skinner-linux:~/dansguard$ ./configure
bash: ./configure: No such file or directory
joe@skinner-linux:~/dansguard$ ./ configure
bash: ./: is a directory
joe@skinner-linux:~/dansguard$ sudo apt-get install dansguardian tinyproxy firehol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tinyproxy is already the newest version.
firehol is already the newest version.
Suggested packages:
  squid
The following NEW packages will be installed:
  dansguardian
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/267kB of archives.
After unpacking 1499kB of additional disk space will be used.
Selecting previously deselected package dansguardian.
(Reading database ... 110106 files and directories currently installed.)
Unpacking dansguardian (from .../dansguardian_2.8.0.6-antivirus-6.3.8-1-1_i386.deb) ...
Setting up dansguardian (2.8.0.6-antivirus-6.3.8-1-1) ...
grep: /etc/dansguardian/dansguardian.conf: No such file or directory
Starting DansGuardian: Error opening /etc/dansguardian/dansguardian.conf
invoke-rc.d: initscript dansguardian, action "start" failed.


 ls /etc/dansguardian
languages  phraselists

any ideas?  should I just install from the source?  If so, how?

---

### Post by freduardo on 2008-04-17
It should already be installed.

```
sudo apt-get install dansguard
```

did the trick ;)

---

### Post by tx-uturn on 2008-04-17
Sorry, i posted more than needed

/dansguard$ sudo apt-get install dansguardian tinyproxy firehol
Reading package lists... Done
Building dependency tree
Reading state information... Done
tinyproxy is already the newest version.
firehol is already the newest version.
Suggested packages:
squid
The following NEW packages will be installed:
dansguardian
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/267kB of archives.
After unpacking 1499kB of additional disk space will be used.
Selecting previously deselected package dansguardian.
(Reading database ... 110106 files and directories currently installed.)
Unpacking dansguardian (from .../dansguardian_2.8.0.6-antivirus-6.3.8-1-1_i386.deb) ...
Setting up dansguardian (2.8.0.6-antivirus-6.3.8-1-1) ...
grep: /etc/dansguardian/dansguardian.conf: No such file or directory
Starting DansGuardian: Error opening /etc/dansguardian/dansguardian.conf
invoke-rc.d: initscript dansguardian, action "start" failed.

---

### Post by tx-uturn on 2008-04-18
anyone have any ideas for me?

---

