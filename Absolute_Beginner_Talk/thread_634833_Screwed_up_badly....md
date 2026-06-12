---
title: "Screwed up badly..."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by poisonkiller on 2007-12-08
Hi!
I tried to install Xubuntu on my computer and dual-boot it with XP Home. When installing, I chose to rezise my old partition (with XP) and resized it to about 40GB (hard drive is 80GB). So, when installer was installing system, I accidentally pressed close button. It was done about 15%. Now I cant boot up XP, partition manager shows, that my half-installed Xubuntu is on a 78GB big partition and my XP is totally gone. How can I restore my old XP installation? I only want my files back, if it's impossible (but it should be possible, cause when partition manager resized, it didn't delete my old partition) I can take most of my old files back from a CD, but some important things were on my XP partition.
Thanks for help, and if you can't understand my text (still learning english :) ), just ask.

---

### Post by KhaaL on 2007-12-08
Hmm, I **think** that the resizing and repartitioning is among of the first things that happens in the installation? 

Anyway, if you can't see the XP partition... Then I'm afraid the files are gone. This is why it's always important to backup data before doing anything that mess with partitions.

PS. your english is not bad!

---

### Post by Ub1476 on 2007-12-08
Boot up a live CD, then check your partitions with this command:

```
sudo fdisk -l
```

---

### Post by louieb on 2007-12-08
Haven't messed with the xUbuntu install CD. Do you have the Live or text based (alternate) install CD?  But at this point your best bet is to get a live CD and try to look at the XP installation on your hard drive. 
Two live CD I know can copy stuff from your hard drive to a usb stick or drive are [Puppy Linux]("http://www.puppylinux.com/") and [Knoppix Linux]("http://www.knoppix.net/").  
Kinda sound like your partition table is messed up there is a tools on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") that may be able to help that is [B]testdisk. 
[/B]A couple of other good rescue links
[TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")
[Rescue FAQ - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Rescue_FAQ")

---

### Post by poisonkiller on 2007-12-08
Okay, I did a testdisk search, and it found 3 NTFS partitions. Now, why are there 3 partitions and how can I fix them?

---

### Post by poisonkiller on 2007-12-08
I give up. I'm currently installing fresh Xubuntu and I've got another question and I don't want to create a new thread. So... how can I enable that mouse Click'n'Drag effect, which you can use to select multiple files?

---

### Post by nawitus on 2007-12-08
Select "view as icons"?

---

