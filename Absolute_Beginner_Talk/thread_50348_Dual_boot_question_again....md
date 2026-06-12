---
title: "Dual boot question again..."
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by bombitmd on 2005-07-20
i've recently downloaded the ubuntu installer but I haven't tried installing it yet. I've been looking all over the net on how to install ubuntu on my current system with windowsXP so that I can dual boot. But most of the ones I've read have already installed them and just ask questions on how to fix this or that. I need the absolute idiot's guide to installing.  :)

I have an old computer (AMD K6-2 450mhz; 128MB, 8 gig HD unpartitioned). I have XP installed. So, how do I proceed? Please show it to me step by step by step. Let me start it  and then just add to the steps. Your help would be GREATLY appreciated!

1. Configure BIOS to enable Boot From CDROM first. 
2. Start computer (with Ubuntu installer in cdrom).

And that's as far as I know what to expect. (Haha! So much for starting it.) From here on... it's all questions:

How do I partition my HD?
Will the ubuntu installation ask me to partition?
Or do I first use GRUB or Partition Magic before running the install disk?
If so, is grub run in Windows, or in DOS? Where do I get GRUB anyway?
Do you recommend reformatting before installing both?
How many partitions and roughly how big (for an 8gig HD)?
After partitioning, I assume it reboots. Then how does the install go? (I'm assuming also that the installation proper is just a series of config questions which, I guess, I can answer on my own.)

So basically, i don't know how to partition my HD and set up a dual-boot.

I know there are lots of forums/articles out there that explain how to set up dual boot for ubuntu and XP. It's just that they still leave me with a lot of questions. I'm really really hoping someone can explain it to me a whole lot simpler. Thanks!

---

### Post by jrev on 2005-07-20
Do you know how to open your BIOS ? this is the first question to answer 
the second is what BIOS type is it ?
you can learn a lot from the command dmesg |less

---

### Post by aysiu on 2005-07-20
If you have Partition Magic, use it. I think Ubuntu has its own partitioning tool, but it's all text-based, not graphical. Other good graphical partitioning tools are QTParted and DiskDrake.

Ok. Step by step.

1. Back up all your data.
2. Make sure you have a spare copy of Windows, in case you need to reinstall.
3. Resize your Windows partition, using Partition Magic, QTParted, or DiskDrake.
4. Hm. An 8 GB hard drive is quite small. I was going to suggest you format a middle partition as FAT32 so you could share files between XP and Ubuntu, but that wouldn't leave much to spare. What does Windows use--4 GB? Ubuntu needs at least 2, I think. Well, anyway, create at least three partitions. One should be a partition of about 256 MB (during the Ubuntu installation, you should use this as the "swap partition").
5. So, here's the breakdown:

4 GB Windows (NTFS)
256 MB for Swap
3.75 GB Ubuntu (EXT3)

6. During the Ubuntu installation, you'll be asked a bunch of questions. Most of them will be easy (what language do you speak?, etc.). When you get to partitioning, select "manually edit existing partitions." Then select the Windows partition and make sure it says "no" to format but "mount" it as /windows. Then, select the swap partition and format it as "linux-swap." Then, select the EXT3 partition, format it as EXT3 and mount it as / ("/" is "root").
7. The other question about grub... after you've set up your partitions, you'll be asked whether you want to install Grub on the MBR. Say "yes."
8. You should be able to dual-boot.

Backing up data is super-important.
I'd also advise that once you've gotten into Ubuntu that you download (through apt-get or Synaptic) the XFCE desktop. Gnome is a little more lightweight than KDE, but for 128 MB, XFCE may be a bit faster.

---

### Post by bombitmd on 2005-07-20
Thanks! Exactly what I needed. I'll try it right away. (I just hope I burned the ISO dile correctly...)

---

### Post by aysiu on 2005-07-20
[QUOTE=bombitmd]Thanks! Exactly what I needed. I'll try it right away. (I just hope I burned the ISO dile correctly...)[/QUOTE] If, for some reason, you didn't--as happened to me the first time I tried Ubuntu--try reburning it at the slowest speed (2x or 4x).

---

