---
title: "uninstall ubuntu/erase or format hard drive"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by cobert on 2007-09-12
I need to uninstall ubuntu or completely erase everything off of a SATA Raid hard drive that i currently have. How do i do so? do i have to do it through the bios, or can i just do it somewhere in ubuntu?

---

### Post by cobert on 2007-09-12
bump... i dont know if that's against the rules or not in this forum but i need some help with this please. don't worry i'm still going to use ubuntu i just need to get it off of this particular hard drive

---

### Post by bodhi.zazen on 2007-09-12
LOL ...

bump after 19 minutes ???

Just format the space to what you want it to be. You can do this with the live CD, launch gparted.

You can delete the partition, making free space, then add the free space to where you want ... with gparted.

If you need to wipe the hard drive, I like dban

---

### Post by Mr_JMM on 2007-10-17
I am trying to erase and re-partition a hard drive using a GParted (live) CD. At the moment there are two partitions; one is a 10GB ext3 which was a root and a 70GB(ish) which was a /home partiton. There is 1.3GB used of the second partition. I can delete both partitions, recreate one primary or two primary partitions, format them to ntfs then again as ext3 no problem.
Except, as soon as I format to ext3 the 1.3GB used data returns. How do I completely erase a hard drive with GParted (beit Gparted live or Ubuntu installation) so that there is no info what-so-ever (other than the little bit each HDD uses for it's own use)?

Many thanks.

James

---

### Post by bodhi.zazen on 2007-10-17
> **Mr_JMM said:**
> I am trying to erase and re-partition a hard drive using a GParted (live) CD. At the moment there are two partitions; one is a 10GB ext3 which was a root and a 70GB(ish) which was a /home partiton. There is 1.3GB used of the second partition. I can delete both partitions, recreate one primary or two primary partitions, format them to ntfs then again as ext3 no problem.
Except, as soon as I format to ext3 the 1.3GB used data returns. How do I completely erase a hard drive with GParted (beit Gparted live or Ubuntu installation) so that there is no info what-so-ever (other than the little bit each HDD uses for it's own use)?

Many thanks.

James

[dban](http://dban.sourceforge.net/)

---

### Post by Mr_JMM on 2007-10-17
Many thanks for that. Will have a look at that later and let you know how I get on.

FWIW I'ill be using the CD version as I don't have an FDD.

Cheers.

---

### Post by GlennW on 2007-10-17
I have been following the thread with interest since I need to erase my ubuntu 7.04 install. I can't get to the desktop and am having troubles at the console too. Due to these issues, I would like to do a clean/fresh install of Gutsy ASAP. Can I simply delete the partition where ubuntu currently resides using Partition Magic 8.0, resizing the rest of the partitions to allow more space for 7.10?

---

### Post by bodhi.zazen on 2007-10-17
> **GlennW said:**
> I have been following the thread with interest since I need to erase my ubuntu 7.04 install. I can't get to the desktop and am having troubles at the console too. Due to these issues, I would like to do a clean/fresh install of Gutsy ASAP. Can I simply delete the partition where ubuntu currently resides using Partition Magic 8.0, resizing the rest of the partitions to allow more space for 7.10?

I would advise against Partition Magic as it does not always play nice with Linux.

Use Gparted : [Documentation](http://gparted.sourceforge.net/documentation.php)

From a live CD (Gutsy or gparted live) !!!

Otherwise, yes.

FYI if Mr_JMM is running dban, it will be a few hours, I usually let it run overnight.

---

