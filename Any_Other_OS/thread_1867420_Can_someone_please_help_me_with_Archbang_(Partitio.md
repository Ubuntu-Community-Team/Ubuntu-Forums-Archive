---
title: "Can someone please help me with Archbang? (Partition)"
date: 2011-10-22
forum: Any Other OS
---

### Post by Dgameman1 on 2011-10-22
Can somebody please help me =[[[
I've been going at this for like 5 hours!!

I go to Disk Preparation
I click Partition by hand and choose the partitions to use because I'm dualbooting with Windows.
It then says, select the disk to partition, I go to /dev/sda
I delete all the old linux partitions i had
I press quit
I scroll down and press Done
It then says select a partition to use as swap.

/sda1 to /sda3 are my windows stuff
The other stuff it says is
/sda5
/sda6
/mapper/arch_root-image

I click sda5 because I don't know what else to click
It asks if I want to format, i select yes

then it asks for me to select the partiton for / (root)
I click /sda6
It then says, "Select the filesystem for /sda6
I pick ext4 out of the options.
It asks if I want to format, i select yes

It then asks if I want to mount other static partitions at bootup ? ?(optional)
I just select done.

It then says this
Continue?
Syntax
--
DEVICE:TYPE:MOUNTPOINT:FORMAT

/sda5:swap:swap:yes
/sda6:ext4:/:yes

I then click yes to continue

It then says
Error creating filesystem ext4 (/dev/sda6)

[IMG]http://img155.imageshack.us/img155/7667/201110221319334742656x3.png[/IMG]

What the ****!!

---

### Post by 23dornot23d on 2011-10-23
Show us what the disk look like using gparted from a liveCD ....

or run boot info script from sourceforge ....

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by [::AP::] on 2012-01-12
Same problem. 

Exactly the same, except on my computer:
/dev/sda1 - Windows 7 Boot partition
/dev/sda2 - Windows 7
/dev/sda3 - Extended
     /dev/sda5 - Swap (Under Extended [/dev/sda3])
     /dev/sda6 - ext4 (Under Extended [/dev/sda3]) (Ubuntu 11.10)
/dev/sda4 - Lenovo Partition (OEM Restore or something)

I am wanting to install Archbang swap on /dev/sda5 and everything else on /dev/sda6. All other partitions left untouched. 

Sorry, I know this thread is a tad old, but it is the only relevant result I recieved from Google.

---

### Post by [::AP::] on 2012-01-12
I just rebooted. 
Installing now.

---

