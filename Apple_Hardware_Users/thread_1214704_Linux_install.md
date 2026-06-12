---
title: "Linux install"
date: 2009-07-16
forum: Apple Hardware Users
---

### Post by n8ek on 2009-07-16
I have tried and tried to install Linux on my intel based apple laptop, here are the problems i have had.

(1) it will not boot any CD/DVD even when i hold down the C key, finally it installed Debian (the only CD it would boot from)

(2) now Debian wont load as with the disks all i get is a black screen after you think it is about to load

(3) i installed refit, still no joy

(4) now since i installed Debian i can no longer see the partition its on so i can at least try and use bootcamp for the install

Is it the laptop or me?

Thanks in advance

---

### Post by maflynn on 2009-07-16
> **n8ek said:**
> I have tried and tried to install Linux on my intel based apple laptop, here are the problems i have had.

(1) it will not boot any CD/DVD even when i hold down the C key, finally it installed Debian (the only CD it would boot from)
Did you try holding down the option key when rebooting.  The C key only works with OSX. Holding the option key will display all bootable partitions

> 
Is it the laptop or me?

You  ;)

Here's what I did and perhaps that will help you.
I booted up OSX, 
Downloaded the ubuntu livecd and burned a disk
Created a partition via Bootcamp
Placed the Ubuntu disk in the drive and rebooted
I held down the option key, waited for the boot menu to display the disk (please note that it improperly displayed the disk as a windows disk)
I selected the disk, booted up Ubuntu
Once I got sufficiently through the install process, I made sure I selected the advanced option of selecting the partition because I wanted to be double sure which partition Ubuntu was going to select.
Installed Ubuntu and was off like a herd of turtles :D

As for rEFIt, I installed it after installed Ubuntu and it worked as advertised. Be sure to follow the directions, its pretty clear cut in getting it to work, once you have OSX and Ubuntu up and running.

If you don't use that, you'll have to always hold down the option key and select the ubuntu partition on reboots.  Not the end of the world but it can get pretty bothersome after a while.

Here's a good resource site for you regarding MacBooks and Ubuntu [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")

---

### Post by n8ek on 2009-07-16
> **maflynn said:**
> Did you try holding down the option key when rebooting.  The C key only works with OSX. Holding the option key will display all bootable partitions


You  ;)

Here's what I did and perhaps that will help you.
I booted up OSX, 
Downloaded the ubuntu livecd and burned a disk
Created a partition via Bootcamp
Placed the Ubuntu disk in the drive and rebooted
I held down the option key, waited for the boot menu to display the disk (please note that it improperly displayed the disk as a windows disk)
I selected the disk, booted up Ubuntu
Once I got sufficiently through the install process, I made sure I selected the advanced option of selecting the partition because I wanted to be double sure which partition Ubuntu was going to select.
Installed Ubuntu and was off like a herd of turtles :D

As for rEFIt, I installed it after installed Ubuntu and it worked as advertised. Be sure to follow the directions, its pretty clear cut in getting it to work, once you have OSX and Ubuntu up and running.

If you don't use that, you'll have to always hold down the option key and select the ubuntu partition on reboots.  Not the end of the world but it can get pretty bothersome after a while.

Here's a good resource site for you regarding MacBooks and Ubuntu [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")

Thanks for the reply,

I did all of the above and now believe it must be a drive issue, now matter what disk i throw at the laptop one's i burn or one's that come with my Linux mag it just will not run the disks fully, what i have to do after putting a Linux disk in the drive is repair the disk permissions using the Mac install DVD as i am unable to boot into os x 

Thanks

---

