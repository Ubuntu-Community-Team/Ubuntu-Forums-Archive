---
title: "dual boot - Adding XP to Ubunto.."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by comintno2 on 2007-08-25
Hello.. I am new!
I am tryin to add XP to my new ubuntu machine... this is apparently not that common in the discussions, but I did find this link.
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

So I finally get my Gparted Cd burned - and I follow the instructions to the point where I have to pick which parition to re size..

I have like 3-6 different partitions and dont know which one to adjust.

I have;
/dev/sda1 Fat16
/dev/sda2 Fat32
/dev/sda3 ext3

etc...

the tutorial says I should adjust the main partiton - which one is that?

Anybody.. please help!!

---

### Post by oilchangeguy on 2007-08-25
why do you have fat 16, and fat 32 partitions?
your best bet is to back up all of your data. install windows first, then ubuntu. this is usally the most problem free way.
see this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Majorix on 2007-08-25
-Put in your XP disk.
-When it comes to where you select the partitions, leave like 15-20 gb for Ubuntu and format the rest to NTFS.
-After you install XP, put in the Ubuntu disk and when it asks you, select "use the largest continuous free space".

When you then boot, everything should be fine.

---

### Post by Gone fishing on 2007-08-25
I've done this when my XP got messed up, I simply deleted the Window partition then allowed Windows install into the free space and afterward repaired Grub using the live cd.

So you could delete your FAT partitions and allow the XP setup program to install into the free space. However, I don't understand your partitions why have you got FAT 16, why use FAT 32 instead of NTFS and where is your Linux Swap partition?

---

