---
title: "Two Drives 1 for Ubantu 1 for Windows"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Thors Hammer on 2006-09-02
Hello:

I have Windows XP Pro loaded on my main drive<80 gig SATA> and would like to install a 2nd Drive<40 Gig IDE> How do I install Ubantu on the 2nd drive and set up the machine for dual booting? I don't want to mess around with repartioning the XP drive or load Ubantu on it.  Thanks.

Cheers:
Thors Hammer

---

### Post by taurus on 2006-09-02
Download the desktop CD (LiveCD) and boot from it.  Click on the install icon and install it on your machine.  When you get to the partition screen, make sure you pick your /dev/hda (IDE while SATA is known as /dev/sda) to install Dapper on it.  Use the defaults partitions and install GRUB on MBR so you can boot both XP and Dapper later.  So basically, just follow the instructions on the screen.  Anf if you are having a problem with your graphic card using the desktop CD (LiveCD), can't see window or screen goes blank, then you should download and use the alternate CD instead.

---

