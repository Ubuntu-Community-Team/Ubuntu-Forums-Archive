---
title: "Installing (K)Ubuntu on External HDD with no internal?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-28
Hi all, I'm trying to get either Kubuntu 7.10 or Ubuntu installed on a machine that has no internal HDD. So I want to install it on my 250GB HDD; my bios does support usb boot. Now here are my problems. I successfully installed Kubuntu however when I restarted grub would try to load then say "error 17." So I thought I just scratch that and give Ubuntu a try. When I click the install icon I choose the partitons I want to use then it goes to install ,but gets stuck at 15% "checking file systems." I do not know where to go from here. If anyone can help me with this I'd greatly appreciate it. Thanks!

Here's the current status of the HDD. 
 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25302   203238283+   c  W95 FAT32 (LBA)
/dev/sda2   *       25303       30274    39937590   83  Linux
/dev/sda3           30275       30401     1020127+  83  Linux

---

### Post by 449 on 2007-11-28
Anyone?

---

### Post by 449 on 2007-11-28
Hm, if nobody can help me with this maybe a mod can move it to a more specific forum? Thanks.

---

### Post by markharding557 on 2007-11-28
check grub is installed on the external hd root partition as your symptoms indicate it may not be.
you can choose where to put grub during installation

---

### Post by Majorix on 2007-11-28
You don't have a swap partition. I believe it's ID was 82.

---

### Post by markharding557 on 2007-11-28
for more info here is link about installing on a removeable drive
[http://www.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw02FireBoot]("http://www.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw02FireBoot")

---

### Post by 449 on 2007-11-28
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25302   203238283+   c  W95 FAT32 (LBA)
/dev/sda2   *       25303       30274    39937590   83  Linux
/dev/sda3           30275       30401     1020127+  82  Linux swap / Solaris

I switched the ex2 to swap in Gparted. 

How do I choose to install grub on the main partition?? :confused:

---

