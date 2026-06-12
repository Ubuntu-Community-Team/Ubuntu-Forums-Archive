---
title: "Installing Ubuntu: gparted problems"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by K3nto on 2007-03-01
I am a windows user and i'm attempting to install Linux (Ubuntu 6.06). I am dealing with a partition problem which can probably be summed up by this screen shot:
[IMG]http://img400.imageshack.us/img400/8553/screenshotbs9.png[/IMG]
I was looking to have around 7gb for the ubuntu install, 2gb for swap (used for hibernation?) and approx 15-20gb for storage. I am using a Dell xps m1210, it uses windows MCE, i have a 120gb hd, 2gb ram, 1.82ghz core2duo.

Any help would be great
thanks

---

### Post by mikewhatever on 2007-03-01
Delete the 2 GB partition and make all the unallocated space an extended partition. Then, create to logical partition in the extended one. The image is from [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by K3nto on 2007-03-01
is the 2gb partition not important then? what does it do?

---

### Post by bigken on 2007-03-01
you can only have 4 primary partitions the only way round this is like mikewhatever says delete the 2gig partition and create and extended partition then make your /system home and swap within the extended partition :)

---

### Post by K3nto on 2007-03-01
i see. do i lose any functionality with my computer if i delete the 2gb partition though?

---

### Post by bigken on 2007-03-01
did you create this partition ?

it could be a ghost imgage to restore your origional OS

---

### Post by bigken on 2007-03-01
also what is the fat 32 partition

---

### Post by K3nto on 2007-03-01
i didn't create it, i know that my computer has a restore partition, and a mediadirect partition (dell's directboot media app) and and a main partition(containing windows).

---

### Post by bigken on 2007-03-01
so you need to know which one holds the restore image do you have the restore cds/dvd

---

### Post by K3nto on 2007-03-01
well i never use mediadirect, and i have the restore disc for that. from what i read, it is in the 1.3-1.4gb range. that would probably show as a 2gb, so i think i will delete that one?

---

### Post by bigken on 2007-03-01
if your sure you have the restore cds I would delete the 2gig and fat32
I would imagine the fat32 to be your restore partition

---

### Post by bigken on 2007-03-01
also you do not need a swap partition as you have 2 gig of ram 

so all you need is yor system and home partitions 

no need to make extended partition 


well I have to go now off too the pub good luck :)

---

### Post by Bartender on 2007-03-01
The message you're seeing is the standard GParted response when you try to create a fourth primary partition.  I've run into it several times.
mikewhatever's advice is sound, because your PC is loaded up with primary partitions and you need to create an extended for Linux.  I'm guessing it's a name-brand PC running Windows Media Center.  If so, one of those partitions (probly dev/sda1) may be a partition that's tied to some of the Media Center functions, and sda4 is probly your recovery partition.  The only way to add a Linux OS to your existing partition map is by creating an extended partition, which acts as a "box" to hold the logical partition(s) where Linux can be installed.  Problem with that is you already have an extended partition.  
So mike's advice is to delete the little extended partition (sda3) and create one extended by combining sda3 and "unallocated".  It appears that there is no data in sda3.  But I'd want to verify that somehow before eliminating it.  I mean, how did it get there in the first place?
You have at least one other option.  What I'm going to suggest is based on the assumption that sda4 is a recovery partition.  You could follow whatever directions are available to you to burn a couple of copies of the recovery partition to a DVD or CD's.  Then, once you're sure you have at least one good copy of the recovery partition, you could delete it.

There's not much point in having the recovery partition sitting there without making copies of it anyway...it's not going to help you if the HDD fails, is it?  "Recovery partitions" are a cost-saving move by the manufacturers that allows them to sell PC's without providing a recovery CD or DVD.  To me, recovery partitions are a rip-off.  How many people know that the first thing they should do with their new PC is copy that partition and save the copy in a safe place?

Anyway.  Once the recovery partition is deleted, you could roll unallocated, sda3 and sda4 together for a roomier Ubuntu installation.  You would gain a primary partition to play with, and the partitioner wouldn't give you the message that has you stuck right now. 
If sda4 is just a partition for storing data, then you could save that data to an external media or drive, or delete it, or copy the important stuff to sda2.  

Many people who dual-boot set up a FAT32 partition for sharing data between the Windows OS and Linux.  A non-bootable data partition doesn't have to be primary.  So, if you do build an extended "box" you may want to set aside some room within the box for a logical FAT32 partition that exists for the purpose of sharing .jpg, .ogg, .odt, etc. files between the two OS'es.

Sheesh - a whole page of give & take while I was writing my thesis

---

### Post by linuxjerk on 2007-04-02
Yes gparted isn't the easiest to use. There has to be better documentation.

---

