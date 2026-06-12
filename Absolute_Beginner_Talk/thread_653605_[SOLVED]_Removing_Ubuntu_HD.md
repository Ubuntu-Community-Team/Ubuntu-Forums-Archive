---
title: "[SOLVED] Removing Ubuntu HD"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Chessmaster on 2007-12-30
Hi there. I am new to Ubuntu and loving it. So far, so good. 

I have a dual boot, with Windows on one HD and Ubuntu on my other HD.

I am having some problems with the Ubuntu drive and I want replace it before it dies completely. Problem is, I cannot take out the Ubuntu drive because the GRUB is on that drive (I think), and hence when I remove it my compute doesn't pick up any drive when I start my computer.

How can I change the settings so it defaults to my Windows drive and I can remove that drive and get it fixed / replaced? 

I have change the GRUB to pick up the Windows drive as the default, but (I suspect) the GRUB is on the Ubuntu drive and hence it doesn't make much difference and I cannot remove that drive. 

Any help / advice, would be appreciated. 

Cheers! 

Tony

---

### Post by nick_h on 2007-12-30
Grub is probably installed in the MBR of your bootable drive anyway.

You can change the default OS by editing the grub menu.lst file:
```
gksudo gedit /boot/grub/menu.lst
```
The default OS is the first entry in the file and the comments explain how to set it. (the numbering starts from 0).

If when you remove your drive you don't boot to grub for some reason you can always re-install it using a Live CD.

---

### Post by meierfra on 2007-12-30
Click on DualTwo in my Signature. (It talks about External and Internal drives, but that is irrelevant). If you follow  that Howto  you will be able to  boot  the drives independently from each other.

---

### Post by candtalan on 2007-12-30
> **Chessmaster said:**
> Hi there. I am new to Ubuntu and loving it. So far, so good. 
I have a dual boot, with Windows on one HD and Ubuntu on my other HD.
I am having some problems with the Ubuntu drive and I want replace it before it dies completely. Problem is, I cannot take out the Ubuntu drive because the GRUB is on that drive (I think), and hence when I remove it my compute doesn't pick up any drive when I start my computer.
How can I change the settings so it defaults to my Windows drive and I can remove that drive and get it fixed / replaced? 
I have change the GRUB to pick up the Windows drive as the default, but (I suspect) the GRUB is on the Ubuntu drive and hence it doesn't make much difference and I cannot remove that drive. 

I believe that the MBR is on the initial area of the windows (booting) hard drive. Grub will be in the boot directory in your linux hard drive as you suggest. I believe the process is that the bios looks at the mbr which is seen to point to the grub directory. 

You have options I think.

You can use the fixmbr facilty from a windows boot disk or CD to instantly revert the mbr to windows only (temporarily :-) ) or you could reconfigure your ubuntu grub so that it resides in its own (small) new partition on the first (windows ) hard drive and so grub will still be valid with only the windows drive. I do not think this is difficult but it may be a stretch for a beginner, and I have only done it myself when initially installing ubuntu (manual install option) which is easy.

---

### Post by Chessmaster on 2008-01-10
Thanks for all your help. 

I backed up the drive, took it out, inserted a new one, installed Ubuntu, restored from my backup, and now it is as if nothing has happened, other than I have a new hard drive. 

Cheers

---

