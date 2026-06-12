---
title: "Triple-booting"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by rth92 on 2007-02-16
hi
i have searched the forum but havent found a solution to my problem. right now i have windows XP and Vista installed, and i want to add ubuntu edgy WITHOUT losing any data. i have Acronis Disk Director Suite and i need to know what file systems or whatever to use. also i have heard that if you have Vista and install Ubuntu you cant boot into Vista anymore? i would really appreciate and help i can get. THANKS

---

### Post by dannyboy79 on 2007-02-16
you coudn't of searched to far or very good because there is a how-to of this. here ya go. and the rumor about not being able to boot into an os anymore is a crock of s__t. grub wiull get ya into any os by eiother direct booting or indirect booting which uses chainloading.. good luck


[http://www.ubuntuforums.org/showthread.php?t=220452](http://www.ubuntuforums.org/showthread.php?t=220452)

---

### Post by rth92 on 2007-02-16
no no i saw that one but right on the third line down it says

NOTE: THIS METHOD DELETES ALL DATA ON YOUR HARD DRIVE.

and i need to keep my data

---

### Post by xpod on 2007-02-16
It also goes on to suggest using the method by Loffe to avoid that.....in the same sentance:)

---

### Post by rth92 on 2007-02-16
yes and if you go there it says

This tutorial guides you through the steps of installing Windows Vista on a computer which already have an Ubuntu installation.

i already have Vista and want Ubuntu...other way around

---

### Post by bodhi.zazen on 2007-02-16
First defragment you HD.

Then boot the Ubuntu CD.

Then partition the HD.

Then install Ubuntu.

:)

Guide : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

There have been mixed reports Re: Booting Vista so you will need to post if ou have problems ...

---

### Post by dannyboy79 on 2007-02-16
well you haven't informed us if you want to use grub or the windows xp boot loader??

if it's grub than ok fine, i guess you're not going to read it yourself and learn and understand how grub works etc etc. what will happen when you install ubuntu onto a partition or hard drive that is free, during the install it'll ask where you want to install grub. you will want to select whatever hard drive is your boot hard drive in the bios (first in order to boot) then it will install grub into the mbr of that drive. Don't worry, it will not affect any of your data nor the installs on that drive! this is easiest because is actually smart enough to see your other installs and add them inside the grub boot list. however, the trick to booting 2 windows installs from the same drive is the fact that you have to hide each  of them from one another. this can be read baout here. and this time, you'll have to read it before I answer of your questions about how to update your menu.lst after you read the link.

it talks about having to hide the windows installs from each other. this is a great thread about booting 100+ os's from 1 grub floppy. ([http://www.justlinux.com/forum/showt...hreadid=143973](http://www.justlinux.com/forum/showt...hreadid=143973)) and here is an example of 1 of his winxp pro's being booted from a seperate hard drive.

# Third disk sda is a Sata with 15 partitions, 9 are bootable

title XP pro @ sdb1
hide (hd0,0)
hide (hd1,0)
hide (hd1,1)
unhide (hd2,0)
map (hd2) (hd0)
map (hd0) (hd2)
root (hd2,0)
makeactive
chainloader +1

---

### Post by rth92 on 2007-02-16
> **bodhi.zazen said:**
> First defragment you HD.

Then boot the Ubuntu CD.

Then partition the HD.

Then install Ubuntu.

:)

Guide : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

There have been mixed reports Re: Booting Vista so you will need to post if ou have problems ...

ok so how do you partition it? i tried to go thru ubuntus partitioner when i tried to install but all it says is unallocated space

---

### Post by bodhi.zazen on 2007-02-16
You can use gparted, ubuntu's partitioner to set up or you can let Ubutnu do it automatically.

The problem you may be having is that you can only have 4 primary partitions.

To get around this, make an extended partition with all of the unallocated space.

Then in the extended partition make a swap partition and an ext3 (root) partitinon.

Size :
swap ram X2, max 1 Gb
root = the rest

Then go ahead and install Ubuntu ...

See here if you want some basic info on partitioning : 

[http://www.ubuntuforums.org/showthread.php?&t=282018](http://www.ubuntuforums.org/showthread.php?&t=282018)

---

### Post by rth92 on 2007-02-16
well gparted livecd just says the whole thing is unallocated space. so i went to acronis and made a 1gb partition for linux swap and 19gb for ext3. now when i go to ubuntu and click install i put manually edit partitions and it still says unallocated space so i just hit forward and it detected the partitions. it said swap was gonna bu put on the 1gb partition and / on the 19. then i clicked install and it said "error: there is no root something selected" or something like that. any ideas? p.s. sorry i dont know much im just new to linux

---

### Post by bodhi.zazen on 2007-02-16
> **rth92 said:**
> well gparted livecd just says the whole thing is unallocated space. so i went to acronis and made a 1gb partition for linux swap and 19gb for ext3. now when i go to ubuntu and click install i put manually edit partitions and it still says unallocated space so i just hit forward and it detected the partitions. it said swap was gonna bu put on the 1gb partition and / on the 19. then i clicked install and it said "error: there is no root something selected" or something like that. any ideas? p.s. sorry i dont know much im just new to linux

LOL

Your partitioning looks good. You can format that free space if yo like and use it for data/storage...

At any rate what you now have is a bug :(

You can either try the alternate CD or this work around:

Ubuquity fails to find /
		[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by rth92 on 2007-02-17
ok - so i downloaded the alternate cd and go thru everything but when i get to the partitions thing it says:

Erase entire disk: SCSI1 (0,0,0) (sda) - 160.0 GB ATA Hitachi HTS
Erase entire disk and use LVM: SCSI1 (0,0,0) (sda) - 160.0 GB ATA
Manually edit partition table

so i select Manually edit partition table and it takes me to one option:

SCSI1 (0,0,0) (sda) - 160.0 GB ATA Hitachi

and it says something about it will delete any other partitions on it. i hope you understand what im saying. and also on the link it says 

Now, when you run the installer, it won't check for a "/" directory, so make sure you have one!

does that mean if i select the partition i want itll install without checking and still wont delete anything else on the drive?

---

### Post by rusty4r on 2007-02-17
Have you backed up your data on cd's or other removable media?

If you have, then go ahead with the desktop CD installer. I wouldn't think you need the alternate cd.

When you get to the partitioning screen it will resize your exising partitions, so it's a good idea to defrag them in advance. 

If you haven't backed up your data, then you should be worried, although I've never had any problems with Ubuntu's partioner damaging data, it just makes since to back it up first and then you'll be free to try whatever you think is appropriate every time you hit next and another question arises.

---

### Post by bodhi.zazen on 2007-02-17
> **rth92 said:**
> ok - so i downloaded the alternate cd and go thru everything but when i get to the partitions thing it says:

Erase entire disk: SCSI1 (0,0,0) (sda) - 160.0 GB ATA Hitachi HTS
Erase entire disk and use LVM: SCSI1 (0,0,0) (sda) - 160.0 GB ATA
Manually edit partition table

so i select Manually edit partition table and it takes me to one option:

SCSI1 (0,0,0) (sda) - 160.0 GB ATA Hitachi

and it says something about it will delete any other partitions on it. i hope you understand what im saying. and also on the link it says 

Now, when you run the installer, it won't check for a "/" directory, so make sure you have one!

does that mean if i select the partition i want itll install without checking and still wont delete anything else on the drive?

Yes, go ahead an use the desktop CD. Select a partition to install root -> should be good to go :)

Here is a guide for the alternated CD if you go that route : 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

