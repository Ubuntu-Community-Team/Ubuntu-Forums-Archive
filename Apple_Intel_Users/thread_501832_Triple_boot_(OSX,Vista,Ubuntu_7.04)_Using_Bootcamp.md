---
title: "Triple boot (OSX,Vista,Ubuntu 7.04) Using Bootcamp Only"
date: 2007-07-15
forum: Apple Intel Users
---

### Post by rami1983 on 2007-07-15
Hi to every one in Ubuntu  Forums ....

I have finish installing the operating systems (OSX, Vista, Ubuntu) using Bootcamp only

my mac is iMac core duo ( 2Ghz   1.5Gb Ram   250GB harddisk)

* I assume you have OSX installed in one partition 233 GB

This the steps as follow

1) Install bootcamp
2) Repartition using bootcamp (I give osx 90GB and Windows 143GB)
3) Ubuntu will take 38Gb+2GB swap out off Windows 143GB
4) Install Windows Vista using 143GB
5) After Installing Windows Vista ... put Ubuntu DVD 7.04 .. restart, hold Option key and select DVD disk to boot from Install using graphical
6) Run Gnome Partition Editor (gparted)  -  use menu System->Administration->Gnome Partition Editor
7) Select the last partition (ntfs) 143GB - right click and select  Resize/Move
8 ) Try to shrink partition to 103GB
9) Now you can install it on the 40GB free ( create 38GB ext3 and 2GB swap) -- you may get error msg .. ignore it ... after finish exit gparted and run it again to be sure it's partitioned
10) Install Ubuntu ............ grub will installed and will chain to Vista/Longhorn 
11) Now Ununtu is installed ... restart ... hold option key
12) you will see OSX and Windows
13) If you boot Windows ... you will see grub menu .. then you can select Ubuntu or Vista :)
14) That is all


Notes:
-------
 - After Ubuntu installed it will eject the DVD and telling to press enter (if no restart happen .. hold the power button to shutdown your mac)
 - Try to boot each operating system .. disk scan will be performed by Windows Vista or Ubuntu or OSX
 - Bootcamp now cannot be restored in single partition ... to restore it .. use Ubunut DVD .. delete the 38GB (ext3) and 2Gb (swap) partitions ... then resize windows partition from 103GB to 143GB
 - Please dont format or play with the 200MB & 128MB between OSX partition
 - If don't follow me ... you can not install Vista ( it will said can not find  suitable cretira)

If any one find it working .. please report you experiance

Thank you

---

### Post by thefockinfury on 2007-07-16
> If don't follow me ... you can not install Vista ( it will said can not find suitable cretira)

i didn't follow this procedure and everything went fine for me. I can't see why this method wouldn't work either, though.

---

### Post by rami1983 on 2007-07-16
> **thefockinfury said:**
> i didn't follow this procedure and everything went fine for me. I can't see why this method wouldn't work either, though.

sorry ... I know it was not clear

I have try to install Ubuntu then install vista ... but when Windows vista see the partition it will see:

200MB -----> this is EFI
90GB ------->this is OSX
38GB ------->this is Ext3
2GB --------> this is Swap
103GB free --> wil used to install vista

Windows Vista will think of this as MBR .. so can not create 5 primary partition .. Will said something like "no suitable criteria" ... because MBR can have only 4 Primary maximum

Also, doing this Bootcamp can not restore this to a single volume 

This disk is formated using Apple GUID .. Windows does not "fully" understand it

my way 100% works and is easy to restore into a single volume ... how ?
  L@@K 

200MB -----> this is EFI
90GB ------->this is OSX
128MB ----->unallocated ( it is actully 512Byte+128MB) 
103GB ------> Windows Vista
38GB ------->this is Ext3
2GB --------> this is Swap

To restore Bootcamp to single volume delete 38GB+2GB and Make Windows Vista Partition to be extended to the free space .. just don not play with the unallocated 128 MB


You can also make your mac as standard pc harddisk .. but you will not able to install OSX
I did it and it works perfectly ... I format the whole harddisk (MBR) using vista install disk and install vista  and it works .. you may be able to install xp,vista and ubuntu ... but you have to find way to install OSX

I you think it was not helpfull ... please, ask more :)

---

### Post by epaulin on 2007-07-16
If I don't create the swap partition, can I create partitions like this:

EFI
OSX
ext3 for Ubuntu 
NTFS for vista

Is Bootcamp the right tool for this job or should I consider diskutil, and the install vista first, then install ubuntu, 

noob question, :) waiting for your reply, tnx.

---

### Post by cyberdork33 on 2007-07-16
I would use diskutil as you can make the partitions any size you want, and as many as you want at once.

---

### Post by thefockinfury on 2007-07-16
>  I would use diskutil as you can make the partitions any size you want, and as many as you want at once.

^^ that's what i did

---

### Post by epaulin on 2007-07-16
If diskutil is what I need, can I still using Bootcamp for triple boot?

Or I only got one choice, rEFIT.

tnx a lot.

---

### Post by cyberdork33 on 2007-07-16
bootcamp uses diskutil to partition.
whether that means it will work or not IDK.

---

### Post by russo.mic on 2007-07-17
to my knowlage, Bootcamp will only allow for 2 partitions.

You have to use refit if you want to triple boot.

---

### Post by rami1983 on 2007-07-17
Gnome Partition Editor (gparted) in Ubuntu Live DVD is perfect ... try to use it

---

### Post by cyberdork33 on 2007-07-17
> **rami1983 said:**
> Gnome Partition Editor (gparted) in Ubuntu Live DVD is perfect ... try to use it

Have you resized a HFS+ volume with it?

---

### Post by rami1983 on 2007-07-17
You can only shrink size
This Feature List

[IMG]http://xs117.xs.to/xs117/07292/Screenshot-Features.png[/IMG]

---

