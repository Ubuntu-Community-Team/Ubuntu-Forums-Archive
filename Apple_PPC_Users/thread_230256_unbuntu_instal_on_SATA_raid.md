---
title: "unbuntu instal on SATA raid"
date: 2006-08-05
forum: Apple PPC Users
---

### Post by rostom on 2006-08-05
Hello,
Is it possible to get ubunut to work on a system with an intel SATA RAID setup?  I'd love to get it working on my system the installer program doesn't see the partitions I've set up on my computer.

Help appreciated.

adam

---

### Post by Ocxic on 2006-08-06
ok. so you want raid you gat a couple options. all these things can be configured during or after install no need to setup the raid b4hand.

1: RAID, during partitioninn you will have the option to configure a raid setup, or you could create the partitions for you system and configure a raid setup after installation

2: LVM (better choice): this allows you to create nad managa groups of filesystems and gives automatic stripping of drives (raid0 / linear) and allows for much more flexiblity in addin space and other drives to you origonal filesystem. again can be configured during partitioning.

and yes ubuntu supports SATA RAID

and my name is Adam too... f*ckin, eh!

---

### Post by rostom on 2006-08-07
thanks for the reply
My issue is that it's a dual boot system and that I've already got intel matrix raid set up.  Ubunutu doesn't recognise the current raid setup and I don't want to format the system.

Any hints appreciated

thanks,

adam

---

### Post by Ocxic on 2006-08-07
is it a hardware raid or software raid you have setup already???

to be honest i don't know how to get you current raid setup working. i have limited knowledge of raid. 

try posting in general support or hardware support.

---

### Post by BoneKracker on 2006-08-10
Here is how you do it...

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

