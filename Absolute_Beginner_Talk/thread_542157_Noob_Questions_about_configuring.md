---
title: "Noob Questions about configuring"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by hiebert on 2007-09-03
I`m new to Ubuntu and i really need some help setting up my computer..
My computer specs are as following

AMD Athlon 64 3000+
ASUS A8N-E
1 Gb RAM
Ati Radeon x1600xt

I would really like to set it right up, as i mentioned before, I'm new here, I'm still using the Ubuntu out of the box, without installing any drivers. Will I also be able to use eye candy software like Beryl? Can someone help? I'm so lost #-o

---

### Post by GMachine_24 on 2007-09-03
ok.. ... since i left my crystal ball at home... i suggest you start by reading...


[https://help.ubuntu.com/](https://help.ubuntu.com/)


there are other install guides

this is an older one... 

[http://doc.ubuntu.com/ubuntu/install/i386/](http://doc.ubuntu.com/ubuntu/install/i386/)

if you search you can find more.

-gm

---

### Post by Kobalt on 2007-09-03
There are many *stickies* at the beginning of the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=73") section, I would suggest you start from there...

---

### Post by hiebert on 2007-09-03
> **Kobalt said:**
> There are many *stickies* at the beginning of the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=73") section, I would suggest you start from there...

I tried the stickies.. They didn't help.. I get error messages.. for example in the ati driver section, i get to step 5 and i get the following error

```
sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.06-2ub untu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I would appreciate your help

---

