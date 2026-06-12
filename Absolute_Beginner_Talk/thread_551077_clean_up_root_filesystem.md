---
title: "clean up root filesystem"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by ceeleelewis on 2007-09-14
It's been a while since i had to manually have to clean up a partition. the command df -k gives ..

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             10000136  10000136         0 100% /
varrun                  965692       300    965392   1% /var/run
varlock                 965692         0    965692   0% /var/lock
procbususb              965692       148    965544   1% /proc/bus/usb
udev                    965692       148    965544   1% /dev
devshm                  965692        16    965676   1% /dev/shm
lrm                     965692     38972    926720   5% /lib/modules/2.6.20-16-generic/volatile
/dev/hda3             46603116   1676716  44926400   4% /home
/dev/sdb2             29207952  15354976  13852976  53% /media/JUSCHRIS
/dev/sda1             33390800        16  33390784   1% /media/SIMPLEVOL1
/dev/sda3             89329432  22043308  67286124  25% /media/SimpleVol3
/dev/sda2             33535360       176  33535184   1% /media/SIMPLEVOL2

is there a way that i can either expand the file system, get a long list of the '/' file system or delete whatever's consuming most of the space ... I assume that the cause maybe vmware .... 

any help would be appreciated

---

### Post by diatribe on 2007-09-14
vmware virtual machines are stored in /var/lib/vmware/Virtual Machines

your / partition is kind of small by the way compared to your home partition

---

