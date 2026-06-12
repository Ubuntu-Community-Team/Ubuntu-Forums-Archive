---
title: "Formatting in BASH, from start to finish - Please help!"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-01-10
Hi there,

I desperately need some help with this please!

I need to know how to format and partition a new hard drive from scratch in an Ubuntu server enviroment. If you're not up to details, i don't mind - just please give the commands or programs and I'll go read up the details on [http://www.ss64.com/bash/](http://www.ss64.com/bash/).

What i think I need is:

1) a command to show all devices connected to the machine sothat I can see where the new drive is, ie /dev/hda or /dev/sdc ?

2) after I know where the drive is, what command/program do I need to use to split the drive into partitions. I have read up on fdisk and cfdisk and I'm still confused. an example would be nice.;) 


Your help will be greatly appreciated!

Thank you,


Rudolf

---

### Post by Bachstelze on 2007-01-10
Just burn a GParted Live CD and use it, it will be far easier ;)

If you can't afford downtime, *sudo fdisk -l* will tell you what your drive is and *fdisk* will let you create partitions.

---

### Post by RudolfMDLT on 2007-01-10
The reason I want to learn how to do it in text is that one of the guys here at work took over from me yesterday and using text commands is as quick as lightning! Using BASH is MUCH more effective than booting up a live disk.

If I wanted to split my drive in 2, one ext3 and the other swap, how would I do it using fdisk?

---

