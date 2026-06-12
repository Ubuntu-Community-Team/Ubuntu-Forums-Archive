---
title: "problem repairing the package catalogue"
date: 2013-11-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pickyuval on 2013-11-05
Hi guys, I'm kinda new to Ubuntu and I noticed that my battery has been draining really fast, I did some checkinh and I understood that bumblebee should help  that, so I installed bumblebee and also tried installing primus (through the terminal) and ever since then the software manager has a problem installing packaged and says it should be repaired or the package needs to be removed.

I have an Asus550jv

I get this log when I try to repair:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 254693 files and directories currently installed.)
Unpacking primus-lib (from .../primus-lib_201303160901git~precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/primus-lib_201303160901git~precise1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/primus/libGL.so.1', which is also in package primus-libs 20130904-1~preciseppa1
Errors were encountered while processing:
 /var/cache/apt/archives/primus-lib_201303160901git~precise1_amd64.deb
dpkg: dependency problems prevent configuration of primus:
 primus depends on primus-lib (= 201303160901git~precise1); however:
  Package primus-lib is not installed.
dpkg: error processing primus (--configure):
 dependency problems - leaving unconfigured

I've already tried :
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update 
sudo apt-get dist upgrade
sudo apt-get autoremove
and when i try "sudo dpkg --configure -a" I get :

dpkg: dependency problems prevent configuration of primus:
 primus depends on primus-lib (= 201303160901git~precise1); however:
  Package primus-lib is not installed.
dpkg: error processing primus (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 primus

I really don't know what else left to do so, please any help would be very appreciated

---

