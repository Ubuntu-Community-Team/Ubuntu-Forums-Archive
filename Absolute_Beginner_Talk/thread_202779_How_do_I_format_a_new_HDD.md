---
title: "How do I format a new HDD"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-06-24
I am running Knoppix 4.0 from the live CD and am currently trying to figure out how to get my Kubuntu to load, Knoppix seems to work fine so I guess it's something with the OS. 

Anyways while I am running Knoppix I have a brand new 80Gb HDD and figured I would format it now.

Are the file systems the same?
What utility do I use to format the HDD?

Obviously I know nothing about Linux so any help would be appreciated...

---

### Post by jazzmuzik on 2006-06-24
You need to partition the hard drive before formatting it. Use fdisk for that. For formatting, there are different programs for that depending on which filesystem you want to use. ext3 is the most common currently. You can use mkfs.ext3 for that.

---

### Post by charles.g.moore on 2006-06-24
So I would just use FDISK, thats simple enough.

I was thinking 20Gb for the system files and the rest for my stuff, this HDD will be a dedicated Linux HDD.

Do I have to worry about creating the partitions without having any OS installed first?

Will the bootloader automatically take some HDD space and move it to the front when I finally do install an OS?

Or does it even work that way?

---

### Post by mfaridi on 2006-06-24
[QUOTE=charles.g.moore]I am running Knoppix 4.0 from the live CD and am currently trying to figure out how to get my Kubuntu to load, Knoppix seems to work fine so I guess it's something with the OS. 

Anyways while I am running Knoppix I have a brand new 80Gb HDD and figured I would format it now.

Are the file systems the same?
What utility do I use to format the HDD?

Obviously I know nothing about Linux so any help would be appreciated...[/QUOTE]

you can use Gparted for partioning your hard disk it is simple 
if you useed partition magic before you can use gparted easy

---

### Post by jazzmuzik on 2006-06-24
[QUOTE=charles.g.moore]I was thinking 20Gb for the system files and the rest for my stuff, this HDD will be a dedicated Linux HDD.[/quote]

I suggest the following four partitions:

/ (root)
/home 
swap (general rule is to make your swap twice the size of your installed RAM)
/extra (for your extra non-OS stuff)

If you want you could add a /boot partition, but it's not really necessary. 100 meg will be fine for that partition if you create it.

Also, 20 gig is probably too much to devote to the OS unless all that extra space will be used for the /home directory.

> Do I have to worry about creating the partitions without having any OS installed first?

You cannot install the OS without having partitions first. The Ubuntu install program goes though a section that gives you the ability to create partitions manually (or automatically). I suggest you go into the manual partition option and get familiar with it. You need to be careful when doing the partitioning and formatting. You don't want to partition or format the wrong drive or partition. Make sure you know the designation of your new 80 gig drive. It will probably be hdb or hdd.

> Will the bootloader automatically take some HDD space and move it to the front when I finally do install an OS?

Or does it even work that way?

I'm not exactly sure how much space the bootloader (grub) takes, but it is negligible and probably only around 1k or so. Info is stored on the boot partition and is not part of the general usable space of the drive.

---

### Post by aysiu on 2006-06-24
Forget all this fdisk stuff.

Kubuntu's own installer has a partitioning part.

Create three partitions during that setup part:

/ (10 GB, Ext3) 
swap (twice your RAM, swap)
/home (whatever's leftover, Ext3)

Then just mount them at the appropriate points.

This will walk you through the process (the only difference being the Kubuntu will be blue instead of brownish-orange):
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by jazzmuzik on 2006-06-24
Yeah, aysiu simplified the instructions pretty well. You don't need to use fdisk unless you are adding a second hard drive and the OS is already installed. Sorry for the confusion. It sounds like you are adding a primary drive, so just go through the install procedure and go into the manual partition section. Add the partitions aysiu mentioned above and you be good.

---

