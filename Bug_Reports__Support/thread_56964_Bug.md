---
title: "Bug ?"
date: 2005-08-14
forum: Bug Reports / Support
---

### Post by galotzas on 2005-08-14
root@galotzas:~ # sudo apt-get upgrade mythtv
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 

It seems to be a funny bug  :)

galotzas

---

### Post by ulisse on 2005-08-14
Sorry, but I can't see anything strange... ;-)
either If you wanted to install or to upgrade mythtv, you should have ran:

apt-get install mythtv

If instead you wanted to upgrade the system:

apt-get upgrade

or

apt-get dist-upgrade

The output you pasted means that there are two broken packages on your system, and if you type Y, apt will try to fix them (without need to download a byte).

The "mythtv" after "upgrade" is totally ignored.

---

### Post by az on 2005-08-14
"2 not fully installed or removed."

This has nothing to do with mythtv.  You need to run

sudo apt-get -f install

to fix whatever you have pending.

---

