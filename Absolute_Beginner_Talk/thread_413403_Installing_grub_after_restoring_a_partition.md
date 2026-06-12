---
title: "Installing grub after restoring a partition"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-04-19
Topic: Installing grub after restoring a partition

Okay, I've done quite a bit of reading up on this matter and had to ask some questions before posting here.  

Here's my situation:

1) Currently dual-booting WinXP and Ubuntu on SATA hdd. PATA hdd used for storing files.

2) Bootloader files for WinXP installed on partition hdc1(PATA hdd) and will be removed. 

3) Grub files for Ubuntu installed in /boot (same partition as Ubuntu)

4) SATA hdd dying so I intend to install only Ubuntu to my PATA hdd for now and send my SATA for RMA. The second partition on my PATA will be repartitioned to make space for Ubuntu. 

5) First, I intend to boot up via Live CD and mount the different partitions. I will not be having a separate /home partition because I intend to restore from a Partimage image file and suspect that I'd need to heavily modify certain files to point everything to /home on a different partition, anyways. 

6) After restoring Ubuntu, I'll be installing Grub via SuperGrub "Restore Grub in Partition". Now, comes my questions.

a) What does it mean by "You should not choose a Windows partition or a partition that has not a boot sector"? Should I backup my /boot folder with Partimage so I can restore it too? Or do I just backup menu.lst and restore it to my /boot folder, though how I'm going to copy a file over without read/write permissions is a bit confounding? 

b) Are there any dangers of SuperGrub destroying my Ubuntu partition?


Thank you! :)

---

### Post by indytim on 2007-04-19
The following link sounds similar to what you are attempting to do.  Hopefully it will get you started.

[Grub-Related]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=15;t=5644;st=0;&#entry39040")

IndyTim

---

### Post by Lucifiel on 2007-04-19
> **indytim said:**
> The following link sounds similar to what you are attempting to do.  Hopefully it will get you started.

[Grub-Related]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=15;t=5644;st=0;&#entry39040")

IndyTim

Thank you for the link. Although, since I don't have a floppy drive(the floppy drive socket on my motherboard died), I'll try copying that into some folder. It's a pity that I can't use my usb drive in place of my floppy drive as my motherboard doesn't support booting from it. 

You know, if it hadn't been for the magnificent support the Ubuntu community is known for, I might have been turned off and stuck to Windows instead. :guitar:

Edit: It seems that instead of backing up the MBR, I could simply instal Grub using SuperGrub. Because, backing up MBR via that method could be a little dangerous as the MBR has a few different parts.

---

