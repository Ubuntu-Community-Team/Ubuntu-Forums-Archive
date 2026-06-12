---
title: "lost windows"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2007-10-16
a friend installed dapper on a windows machine now he cannot find his windows files please help.
any suggestions? he is upgrading to feisty by changing sources list now will feisty be able to find windows providing he did not reformatt the whole hd while installing dapper?

---

### Post by annda on 2007-10-16
first of all, tell your friend NOT to upgrade or do ANYTHING to his HDD.

this is a good tool for recovering lost partitions:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
and for best results it SHOULD be used with a live CD - boot from live CD, install testdisk from the repositories (at least Feisty has it).

can your friend even find the windows partition from a live CD? ubuntu, gparted, whatever? if not, testdisk is the way to go.

if he/she can, they can use this guide:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by vikram on 2007-10-16
If your friend formatted the whole HD I think he is out of luck.

are the windows partition visibile ?

try 
sudo fdisk -l
to get a list of partitions

upgrading to fiesty may not be required to recover windows data but I'd suggest to upgrade to edgy then fiesty

---

