---
title: "Dual boot"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Al9 on 2007-04-19
Hi. Aboslute newbie to Linux. I obtained the Ubuntu 6.06 CD and have been running it from the CD. Love the way it works and would like to install it to my hard drive but I am scared stiff that I will lose access to my Windows programs if I proceed. I have a lot of programs there which are not available in Linux and just cannot afford to lose them. There is nothing in the install procedure so far which tells me I can boot either to Windows XP or to Linux. I have partitioned and formatted two sections of the second hard drive to load Linux and then after doing that the Ubuntu procedure seems to stop. Can anyone confirm that there is something (perhaps later?) in the installation procedure which will allow me to keep vital access to Windows and yet still allow access to Linux? I can't find any reference to this anywhere in this forum.
TIA

---

### Post by munky-head on 2007-04-19
Of course!
There are many guides online about configuring GRUB (the boot selector thingie) and adding Windows XP to it. I did it, it works flawlessly. It's so comprehensive that you can find guides about how to configure it in both systems, and according to 'which was there first' as well.
Also, I have been told by someone that 3rd party software such as Acronis OS selector make it even easier, yet I haven't found the need to use it.

---

### Post by LaRoza on 2007-04-19
When you have two operating systems on a single computer, you choose which one to boot at start up.

If you only have one OP at the moment you do not see this screen.

---

### Post by dptxp on 2007-04-19
I have not seen 6.04, I use 6.10, now shifting to 7.04. There we start with 'Install' from desktop,use resize after deleting the free space,  provide 4 to 8 GB for root (EXT3 format), 2+ GB for SWAP and rest for data (FAT32 if you want Windows also to read the data, else EXT3).
In next box we ensure that the Windows and the Data partitions are not formatted and the new ones are formatted. Ensure that the correct ones are set for root and swap.

---

### Post by Surgeon General on 2007-04-19
> **Al9 said:**
> Hi. Aboslute newbie to Linux. I obtained the Ubuntu 6.06 CD and have been running it from the CD. Love the way it works and would like to install it to my hard drive but I am scared stiff that I will lose access to my Windows programs if I proceed. I have a lot of programs there which are not available in Linux and just cannot afford to lose them. There is nothing in the install procedure so far which tells me I can boot either to Windows XP or to Linux. I have partitioned and formatted two sections of the second hard drive to load Linux and then after doing that the Ubuntu procedure seems to stop. Can anyone confirm that there is something (perhaps later?) in the installation procedure which will allow me to keep vital access to Windows and yet still allow access to Linux? I can't find any reference to this anywhere in this forum.
TIA

Hi, you said you have already repartitioned and reformatted your hard disk? Can you confirm if you can still boot with Windows?

---

### Post by rillip on 2007-04-19
There is no prompt in the setup procedure that covers this; it just happens by default.

Here's a typical install process:

pop in live cd.  Everything is great, you decide to install.

You go through, chose your time zone, choose your partitions, choose your username and password, etc.  Eventually, step six I think, you start actually installing the files.  Then it tells you to reboot.

When you reboot, you'll see an unfamiliar screen come up with a text menu.  This is Grub, a bootloader that got installed.  In there, you will see choices for your Linux versions AND Windows.

I did this with Win 2000 and had zero problems.  If you search for "win xp instalation" or "dual boot xp" in this forum I gaurentee you'll find other people who have had the same types of question.

There is no danger to your aps.  The only danger is that your MBR is overwritten to use grup.  This is an issue for a very small percentage of people. Typically, letting grub do it's thing works 100% without issue.

---

### Post by tbasherizer on 2007-04-19
All you have to do with the Feisty live cd is click "install" on the desktop, then follow the manual partitioning wizard, making sure your windows drive/partition is untouched. The installer configures GRUB for you. But whenever dual-booting, I have found it much easier to install windows first, then Ubuntu from a GRUB standpoint.

---

### Post by N Clement on 2007-04-19
Yes, installing a new OS is always a little thrilling (why I have done it far too many times:) ).  The good thing is, it is really not dangerous at all.  If you have Windows installed first, and are absolutely sure that you are not reformatting the xp partitions(s), then you are fine.  What will happen is this:

1)  Ubuntu will install on those other patitions on your second hard drive; it will not touch xp, provided you told it not to touch xp.

2)  It will overwrite the first sector of your master hard drive, called the Master Boot Record.  Don't worry, this does not contain any part of your XP system.  All the MBR does is tell the system where the (up to) 4 primary partitions on your hard drive are and where to go to find the boot program.

3)  It will install something called Grub (GRand Unified Bootloader) which is software to let you choose between boot options after Bios hands over controll to the MBR (BIOS->MBR->Grub->you choose).

The key thing here is that you don't reformatt the windows partiton(s).  If you avoid this, you have essentially nothing to fear.  Even if Linux or Grub is totally hosed, all you have to do is use your XP install CD to restore the MBR to factory settings, or the Ubuntu CD to fix it back to the Grub configuration.


***Bottom Line***
DON'T REFORMATT WINDOWS

---

### Post by Seisen on 2007-04-19
Its easier to install Windows first because when your done installing Ubuntu it will find you Windows OS and add it to the grub menu.

---

### Post by Al9 on 2007-04-19
Thanks to all for your very prompt replies! Most impressive. I'll give it a shot...

---

