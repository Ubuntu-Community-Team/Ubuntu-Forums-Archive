---
title: "install multiple linux distro"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2007-06-11
Dear Friends,

I have been using Linux for some time now, but I am not a technical expert. I am purely an user. 

I tried to install two different linux distro in my desktop (Xubuntu and Sam linux). However I aborted the installation process as I encountered some doubts - 
1. I made two partitions for the two distros - but I could not understand how to mount them. I mounted both as "/", But when I proceeded I got an warning that two partitions are mounted as root - so I aborted the installation as I got confused.

2. I had created two more partitions - one for "/home" and the other for "Swap".

I want to know:

1. can I use common "/Home" and "Swap" partition for more than one distro?
2. How to mount the other two parti tions where I install the two linux distros? or is there any other alternative to install two different distros.

Thank you very much. 

Raj

---

### Post by mcduck on 2007-06-11
1. Yes, you can share both /home and swap partitions between different linux distros.

2. You can't share root. And there can only be one root. Also, the partition settings are different for each instaled distribution. I recommend mounting other distribution's root partition inside /media:

In Xubuntu:
partition 1 - /
partition 2 - /media/sam
partition 3 - /home
partition 4 - swap

In Sam Linux:
partition 1 -/media/xubuntu
partition 2 - /
partition 3 - /home
partition 4 - swap

---

### Post by timcredible on 2007-06-11
I do exactly what you're looking to do.  i have 4 partitions:

partition 1: ubuntu 6.06 root partition
partition 2: ubuntu 6.10 root partition
partition 3: swap
partition 4: /home

what you need to do is define only one root partition (/) per distro boot config file.  So, when i boot into ubuntu 6.06, partition 1 is / and partition 2 is /ubuntu610.  when i boot into ubuntu 6.10, partition 1 is /ubuntu606 and partition 2 is /.  the only tricky part is how to choose between the 2 distros.  the easiest is to use the CONFIGFILE option in menu.lst, which will allow grub to read the other partition's menu.lst.  what happens is you install distro 1, then install distro 2.  at that point, only distro 2 menu.lst file is read.  the CONFIGFILE option will allow you to choose the other distro easily.  i'm not on that machine right now, but a search should find what you need.

---

### Post by pospam on 2007-06-11
Hi all:
I want to extend the original question.
I currently double boot windows XP and Ubuntu I would like to
triple boot Xp-Ubuntu-Test distro.
I just want to be able to have the option to install other linux distros to give
them a test drive (i know that I can use liveCds but I rather try them at full speed
for a truthful comparison) without messing up my ubuntu install.
How should I Partition my hard disk?
THis is my current setup:
Partition 1-ntfs-Xp
Partition 2-ext3-home (for Ubuntu)
Partion 3-ext3- / (for Ubuntu)
Partition 4- swap.

What changes should I do and what partitions should I add in order to be able to triple boot?
Thanks for help.
P.

---

### Post by clinto on 2007-08-18
@posam
I'm hoping you made another thread to address your question by now. Since I came across it and no one answered it, I thought I would just throw in my two.

If you want to add another partition for another distro, you must have un-partitioned space. If not, you have to shrink one of your partitions to make room for another one. Use Gparted.

---

