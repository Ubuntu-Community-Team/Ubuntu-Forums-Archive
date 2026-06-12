---
title: "Serious Dual Boot Issue"
date: 2009-04-05
forum: Apple Hardware Users
---

### Post by RDHerm on 2009-04-05
I have an Intel-based Mac laptop that I was trying to set up to dual-boot Leopard 10.5.5 and Ubuntu 8.10.

Leopard was already installed, so I created a new partition on my hard drive using the partition utility on the Ubuntu install disk and installed Ubuntu on it. And then my troubles started.

After restarting the computer, I found I was unable to successfully boot into either Leopard or Ubuntu. If I try to start up like normal or boot into safe mode, I get a grey folder icon with a question mark on it that flashes repeatedly on the screen. If I restart and try to bring up the boot menu, I get a cursor on the screen, but nothing else. 

Does anyone have any idea what I need to do to fix this?

---

### Post by pxwpxw on 2009-04-05
> **RDHerm said:**
> I have an Intel-based Mac laptop that I was trying to set up to dual-boot Leopard 10.5.5 and Ubuntu 8.10.

Leopard was already installed, so I created a new partition on my hard drive using the partition utility on the Ubuntu install disk and installed Ubuntu on it. And then my troubles started.

After restarting the computer, I found I was unable to successfully boot into either Leopard or Ubuntu. If I try to start up like normal or boot into safe mode, I get a grey folder icon with a question mark on it that flashes repeatedly on the screen. If I restart and try to bring up the boot menu, I get a cursor on the screen, but nothing else. 

Does anyone have any idea what I need to do to fix this?

Sound like you need to run a refit cd to make osx bootable and then probably reinstall grub to boot linux.
See the Intel Mac faq sticky and two other threads right near yours.

---

### Post by cyberdork33 on 2009-04-06
Please checkout the install wiki:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by deltaiscain on 2009-04-06
gray folder with the question mark? Ouch, I hope you have a backup. Either you wiped OS X when you installed Ubuntu, or your hard drive failed. You could insert the OS X cd and use disk utility to verify the disk.

---

### Post by cyberdork33 on 2009-04-06
> **deltaiscain said:**
> gray folder with the question mark? Ouch, I hope you have a backup. Either you wiped OS X when you installed Ubuntu, or your hard drive failed. You could insert the OS X cd and use disk utility to the disk.
wrong. This is a known issue (that will hopefully finally be fixed in Jaunty Final). You need to sync your parrtition tables with the refit cd, or with gptsync

---

### Post by deltaiscain on 2009-04-06
> **cyberdork33 said:**
> wrong. This is a known issue (that will hopefully finally be fixed in Jaunty Final). You need to sync your parrtition tables with the refit cd, or with gptsync

He installed Ubuntu Intrepid Ibex 8.10, not Jaunty Jacklope 9.04.

---

### Post by cyberdork33 on 2009-04-06
> **deltaiscain said:**
> He installed Ubuntu Intrepid Ibex 8.10, not Jaunty Jacklope 9.04.
I know that. Thanks.

---

### Post by shike1988 on 2009-04-06
hi i am also new to Ubuntu and i have a similar problem. I have a HP Pavillion dv6707us and i am trying to Dual boot Ubuntu and XP on the system. I have not used a linux system since before windows 95 launched. I have my hard drive partitioned with 44 gigs free for XP and 100gigs for Uuntu. my friend told me to look up wiki ubuntu for directions but i can not find any. could someone help me get a ready set of directions for turminal so i can install xp.

---

### Post by cyberdork33 on 2009-04-06
> **shike1988 said:**
> hi i am also new to Ubuntu and i have a similar problem. I have a HP Pavillion dv6707us and i am trying to Dual boot Ubuntu and XP on the system. I have not used a linux system since before windows 95 launched. I have my hard drive partitioned with 44 gigs free for XP and 100gigs for Uuntu. my friend told me to look up wiki ubuntu for directions but i can not find any. could someone help me get a ready set of directions for turminal so i can install xp.
you will want to install Windows first. (PS, this is a forum for Apple hardware)

---

