---
title: "Dual Boot, 2 HDs, XP Won't Boot"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by joeyt2k on 2007-08-31
Total Linux noob running a P4 Vaio, 2.8 GHz, 512 RAM.

Popped out my old XP HD, installed Ubuntu on a new drive, popped XP back in. 

So now:

Ubuntu installed on 40GB Master, XP on 120GB Slave. Pins are configured correctly for this setup.

XP HDs show up in Ubuntu. Grub recognizes Windows in its menu, but when I pick it I either get a Starting Up .... screen that just freezes, or a "Starting Sony Vaio System Recovery Powered By Windows" screen followed by a solid blue screen.

I have read every post on this subject I can find, tried about 20 different GRUB settings, tried switching Master and Slave. 

Right now, with Ubuntu Master and XP Slave, I have GRUB set to load Windows by default. Rest of it looks like this:

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=bc46cbda-5bff-4f51-acee-d21f637d4d17 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=bc46cbda-5bff-4f51-acee-d21f637d4d17 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=bc46cbda-5bff-4f51-acee-d21f637d4d17 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=bc46cbda-5bff-4f51-acee-d21f637d4d17 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

title           Windows XP
root            (hd1,0)
makeactive
chainloader     +1 

Again, the Windows entry is just the most recent of several I've tried based on forum posts.

Any help, or direction to a post I may have missed, is greatly appreciated. Feel free to talk to me like I'm a small child.

---

### Post by rsambuca on 2007-08-31
This is a very difficult way to run your system.  XP really doesn't like to run as the non-primary drive.  Also, by removing the XP drive prior to installing ubuntu, it prevents the ubuntu grub loader from seeing XP, and thus it can't set up properly.  The windows that it is seeing is the hidden recovery partition that came with your pc.

I would recommend putting your XP drive back as the master, and remove the ubuntu drive.  Make sure that XP loads and runs.  Then I would put the smaller drive on - set it up as a slave drive - and then install ubuntu onto that drive.  Have the grub loader put itself onto the XP drive MBR, and you will be prompted at bootup whether you want XP or ubuntu.

---

### Post by cascadia4 on 2007-08-31
If you have a live CD installed, I'd start by running that and seeing what you can find. I'd also consider reformat/reinstall both Ubuntu and Windows XP on their respective disks. Of course, you'll want to make sure you have both HD's configured for master/slave as you want.

Just my 2 cents.

---

### Post by edwardLS on 2007-08-31
If I understand you correctly, you had the HDD containing XP out of the system when you installed ubuntu on a different HDD.  You then put the XP HDD back into the system.  

If this is the case, I believe you may have the various pieces of the OS'es (XP and ubuntu) located in different places than what the two systems are expecting.  That is, XP was on the first HDD in your system.  You then made the ubuntu HDD the first drive in your system, and now when you put the XP HDD back into the system it becomes the second HDD.

I have installed ubuntu many times is learning how it goes, and I still don't know it all.  I would suggest that you put just the XP HDD into your system an see if you can get back to a functioning XP system.  If that works, put the second HDD (the one you want for ubuntu) into the system with the XP HDD still in the system.  Then re-install ubuntu.  When you get to the Partiioning section of the installation, do a Manual Partition.  Carefully select the second HDD and do whatever you want on the HDD to install ubuntu.  There is a box to check/uncheck for formatting.  Make sure the ones for XP are UNCHECKED.  You probably will want the ones for ubuntu CHECKED.

Good luck.

---

### Post by dstew on 2007-08-31
rsambuca speaks the truth. It is possible to get your Windows XP to boot, but I guess you have tried all the permutations, including the map statements, right?

I agree that you should start over, and leave the XP hard disk in when installing Ubuntu and grub.

---

### Post by joeyt2k on 2007-09-01
Thanks to all for the prompt advice.

As per the group's recommendations ...

With both HDs plugged in, I wiped the Master, reinstalled Windows, then reinstalled Ubuntu onto the Slave, and GRUB did the rest. The only GRUB line I had to edit, for my own personal convenience, was the time before the menu autoloads an OS. 

Thanks again.

---

