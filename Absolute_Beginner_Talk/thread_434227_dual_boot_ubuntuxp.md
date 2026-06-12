---
title: "dual boot ubuntu/xp"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-05-05
I am going to install ubuntu 7.10 64 amd on my xp system.  I have 4 partitions:C ntfs 65 G, D ntfs 8.5 G (recovery), J ntfs 107G, and K ntfs 53G.  Do I have to partition manually, or can I choose the J partition and have Ubuntu install automatically?  In the manual mode, how helpful is the interface?  Do I partition the J drive into a swap partition (4G) and root for the rest of the partition?

I tried installing Suse 6.0 several years ago on another machine and lost 30gigs.

Thanks,
Cygnis 1

---

### Post by Happy_Man on 2007-05-05
Right, so am I correct in assuming that you have four partitions, and you would like to install to the one with 107 gigs of space? If so, then yes, I would suggest partitioning manually. It's not hard; First, boot from a livecd and go into the installer, when you get to the step in the installer that asks how you want to partition, choose "manual" and delete the partition with 107 GB; then right-click, choose new, and then create an extended partition. Afterwards, right-click in the gray part again, and choose to create a new ext3 formatted partition, then resize it so you have an extra gig hanging at the end that is unallocated. Use that gig to make a new swap partition (formatted linux-swap) and you're done!

---

### Post by sarcazmo on 2007-05-05
Sorry to hijack the thread I just have a quick question.

I have XP installed, do I need to manually create a partition using something like partition magic?  Or can I choose the option to use the "Largest continuous free space" and will that do the partitioning for me?

---

### Post by Happy_Man on 2007-05-05
Yeah that will work. Don't worry, I did that my first time, and everything went perfectly. Of course, I promptly killed my install, and then reinstalled about fifty times. But that's a whole 'nother story. ;)

---

### Post by houstonbofh on 2007-05-05
Keep in mind that there is a limit of 4 primary partitions.  If you have 4 primary partitions now, you can not create more.

---

### Post by crimesaucer on 2007-05-05
This guide has a lot of helpful information: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

and the home page of it: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by antoz on 2007-05-05
I would also add a "home" partition that way if you need to reinstall for some reason or an other you keep all your files and settings.
"/" ubuntu 
"swap" Swap partition 1.5 times your ram
"home" for your files etc...
the links in the previous post are very helpfull, here is an other good one
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

