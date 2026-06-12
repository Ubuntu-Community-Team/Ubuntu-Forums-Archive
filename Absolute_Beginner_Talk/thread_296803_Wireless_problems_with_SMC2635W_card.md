---
title: "Wireless problems with SMC2635W card"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-10
I have several problems with my SMC2635W NIC:

1) Rarely will my NIC (interface ra0) be activated when I boot up my laptop

2) After activating my NIC, the light will go on, but will struggle to connect to the internet. After playing with my dns server IP's (which enjoy to change and reset regularly), it will connect to the net. (I am connected to the net now)

3) Today, I have not been able to connect gaim to the net (although I can connect amsn to the net) or install any files from synaptics.

Does anyone know how to fix any of my  problems?

I love Ubuntu and wouldn't consider switching to another OS, but the wireless aspect of it could be better ;)

Cheers

---

### Post by spamzilla on 2006-11-10
Here's the output when I try to install something. Maybe this will help in getting some of my problems solved:

```

matt@matt-laptop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  debconf-utils debhelper html2text libbeecrypt6 librpm4 rpm
Suggested packages:
  lsb-rpm lintian dh-make
The following NEW packages will be installed
  alien debconf-utils debhelper html2text libbeecrypt6 librpm4 rpm
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 1756kB/2388kB of archives.
After unpacking 7913kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Errhttp://gb.archive.ubuntu.com dapper/main libbeecrypt6 4.1.2-4
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://security.ubuntu.com dapper-security/main librpm4 4.4.1-5ubuntu2.1
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://gb.archive.ubuntu.com dapper/main alien 8.64
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-security/main librpm4 4.4.1-5ubuntu2.1
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-security/main rpm 4.4.1-5ubuntu2.1
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/beecrypt/libbeecrypt6_4.1.2-4_i386.deb  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-5ubuntu2.1_i386.deb  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-5ubuntu2.1_i386.deb  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/alien/alien_8.64_all.deb  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by spamzilla on 2006-11-10
Bump. I just restarted and it took me about 30 mins after playing with my dns server to get connected to the net. Does anyone know how I could perma solve this?

---

