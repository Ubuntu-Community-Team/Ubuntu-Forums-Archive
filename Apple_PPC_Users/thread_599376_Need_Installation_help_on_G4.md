---
title: "Need Installation help on G4"
date: 2007-11-01
forum: Apple PPC Users
---

### Post by ruff2112 on 2007-11-01
I have a Powerbook G4 with 1ghz CPU, 1Gb ram and 55GB HD. 

This laptop OS progression was:
OS9 -> OSX Tiger -> OSX Leaopard

In OSX, my partition shows 2 drives:
OSXDiskDrive 45 GB 
Free Space    10 GB 

I want to install Kubuntu 6.06 on this laptop (I want the KDE Windows like desktop) in its 10 GB free space but when I boot the Kubuntu live CD, it shows this as the partition map in Qparted:

   Name                 Type           Size (gb) 
1   /dev/hda1         Unknown    .03 
2   /dev/hda2         Unknown    .03 
3   /dev/hda3         Unknown    .03 
4   /dev/hda4         Unknown    .03 
5   /dev/hda5         Unknown    .03 
6   /dev/hda6         Unknown    .25 
7   /dev/hda7         Unknown    .25 
8   /dev/hda8         Unknown    .25 
9   /dev/hda9         hfs+            45 
10 /dev/hda10       free             10

If I go to QParted, I am NOT able to re-partition the free space into 2 seperate partitions (one for Kubuntu and one for swap file). It only allows me to select "property" in QParted when  I select the free space. I think this is due to the 4 partition limit, but I am not sure of this?

I have no idea what the first 1-8 partitions are, and why they are there in the first place. 

If I tell Kubuntu to use all the free space during installation, will the installer be able to create the seperate swap file partition, even thought Qparted cannot? 

Thank you for your help.

---

### Post by seatea on 2007-11-01
I believe the installer will need to create 3 partitions. One, a boot partition for yaboot; two, the root and home partition; and three, a swap partition. Technically, you  could omit the swap, but it may help if memory use becomes extensive. The installer should do all this automatically. My computer also has several partitions associated with Mac OS X.

---

### Post by ruff2112 on 2007-11-01
So if I choose "install to largest available free space" from the installer, it will install into the 10GB free space on the drive and it will automatically create those partitions, even though I cannot manualy do it from QParted? I am just not sure what the installer uses to create those partitions. 

If it is using QParted behind the scenes also, I do not see how it can create those partitions but I cannot manually.

---

### Post by seatea on 2007-11-02
I haven't tried to use qparted to  create the necessary partitions, but the Live CD should do the job however it operates. I think you have to use  the Alternate CD to manually make the  partitions.

---

