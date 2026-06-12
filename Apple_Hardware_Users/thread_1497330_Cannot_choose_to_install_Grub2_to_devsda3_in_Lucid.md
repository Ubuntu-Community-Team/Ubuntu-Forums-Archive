---
title: "Cannot choose to install Grub2 to dev/sda3 in Lucid?"
date: 2010-05-30
forum: Apple Hardware Users
---

### Post by EchohcE on 2010-05-30
I had been using Karmic with a dual-boot of Leopard and Ubuntu 9.10 64-bit with rEFIt.  Something apparently cracked when I tried to upgrade to 10.04 LTS using the Update Manager, and I was left with an odd message when trying to boot into it using rEFIt.  I've deleted all the ubuntu partitions I had and attempted to reinstall manually using a LiveCD.  Everything went smoothly until I got to the final confirmation page.  I selected Advanced, checked Install bootloader, but I can't choose dev/sda3.  Here are my options:

dev/sda
dev/sda1
dev/sda-1
dev/sda2                  Macintosh HD
dev/sda-1

Another thing I don't understand....see how dev/sda-1 appears twice?  After reading up, I also see that I may be using the un-respun version of Lucid, therefore errors may be present, but I have no way of confirming whether or not mine is an affected LiveCD.  Any help would be greatly appreciated.

---

### Post by jamesixgun on 2010-05-30
Many of us (me included) have come upon this problem. 

[Here]("http://ubuntuforums.org/showthread.php?t=1297229&page=8") is my rewording of a solution developed by Jacques4x4 (credit where credit is due).

It should work just fine.

By the way, I have no idea why the installer creates the partition map it does (with two times dev/sda-1). I also have no clue how to tell if yours is the respun or affected LiveCD. In fact, I've not heard anything about a respun version, but I haven't been looking for one since I got mine to work with the above instructions.

---

### Post by EchohcE on 2010-05-30
My apologies.  I was referring to the bug found before the release.  Canonical decided to push back the release a few hours while they respun it.  It probably is not a problem now.

---

### Post by linux-hack on 2010-05-31
> **EchohcE said:**
> I had been using Karmic with a dual-boot of Leopard and Ubuntu 9.10 64-bit with rEFIt.  Something apparently cracked when I tried to upgrade to 10.04 LTS using the Update Manager, and I was left with an odd message when trying to boot into it using rEFIt.  I've deleted all the ubuntu partitions I had and attempted to reinstall manually using a LiveCD.  Everything went smoothly until I got to the final confirmation page.  I selected Advanced, checked Install bootloader, but I can't choose dev/sda3.  Here are my options:

dev/sda
dev/sda1
dev/sda-1
dev/sda2                  Macintosh HD
dev/sda-1

Another thing I don't understand....see how dev/sda-1 appears twice?  After reading up, I also see that I may be using the un-respun version of Lucid, therefore errors may be present, but I have no way of confirming whether or not mine is an affected LiveCD.  Any help would be greatly appreciated.

I had the same problem and to fix this you need to partition with gparted before installing and make a sda3 to install grub on.

---

### Post by EchohcE on 2010-06-03
Thanks guys.  How do I mark the thread as solved so I don't waste the mods' time?

---

### Post by charli_e on 2010-09-01
> **boogy9 said:**
> I had the same problem and to fix this you need to partition with gparted before installing and make a sda3 to install grub on. 

Im tryin to install Ubuntu 10.04.1 LTS on MAC PRO, and  that steps and I can't find the sd3 to install it.. I used bootcamp to create the linux partion.

Then I'm on the same problem but [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") solution is not so user friendly I guess.

Can you tell some more about create the sda3 by gparted? size?

---

### Post by charli_e on 2010-09-01
so finally , After spend many hours following wierd solutions to solve the bad boot loader and others, I've tried againg to install manually Linux 10.04 ... as it was : 

dev/sda
dev/sda1
dev/sda-1
dev/sda2                  Macintosh HD
dev/sda-1

Then folowing the commented steps, when is time to use gpart to create the 2 partitions:
 The point was 
1- add first the with gparted the swap partirtion, 2*RAM, say SWAP 
2- add the main partition to ubuntu and '/' selected.

 That's all folks!

---

