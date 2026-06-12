---
title: "[SOLVED] Kernel Panic After Installing 7.10"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by rav26 on 2007-11-10
Hi,

I just installed Gutsy on my slave harddrive, using windows as my primary harddrive. After the installation, I restarted my computer, changed the bootorder and then let the computer boot itself in. 

When I get to the GRUB loader, I am prompted with 4 options:
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
Windows Vista/Longhorn (loader)

When I try clicking onto the first option (Ubuntu 7.10, kernel 2.6.22-14-generic)
I get a message that says,

Starting up ...
Kernel panic-not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I restart the computer and then i try editing the kernel, but to no avail

root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d3a93fbc-d8dd-42c9-8f31-7b68d53fa202
initrd /boot/initrd.img-2.6.22-14-generic
quiet

Is there something that I am doing wrong?

When I click on the fourth option, I can boot into Windows XP fine.

---

### Post by matthewcraig on 2007-11-10
If you are not able to switch back your changes to grub.conf, then you may have to re-install Ubuntu.  Although, Maybe someone else on the forum will think of another way to troubleshoot this issue.

---

### Post by rav26 on 2007-11-10
That was what I was wanting to do or what not. But now, I can't even use the DVD-ROM to boot my Ubuntu DVD. Before when Ubuntu was not installed, I can just restart my computer from Windows and then the DVD will boot automatically prompting me to options from Ubuntu. But then now that I have installed Windows on the primary and Ubuntu on the slave, I can't seem to boot from the DVD anymore.

---

### Post by matthewcraig on 2007-11-10
Ohhhh!  You installed Windows after Ubuntu?  Might have mentioned that in the first post.... ;)

That explains it.  Yeap, Windows kills your boot sector.  Reinstall Ubuntu.

---

### Post by rav26 on 2007-11-10
Oh... no that's not what I meant.

I installed Windows XP on my primary drive. I already have Windows XP on my slave drive, and when I boot Ubuntu DVD, I used the guided partition and deleted the partition from the slave. So then Ubuntu is on the slave drive with Windows as the primary. 

That being said, I installed Ubuntu after Windows.

---

### Post by arashiko28 on 2007-11-10
I had a similar problem, I can't install ubuntu, not even run the live cd. It's my dad's computer, I used to test 7.04 Ubuntu, Xubuntu and Kubuntu on it. Now, I tried to install 7.10 and it doesn't even boot. it shows that kernel panic message :confused: the computer has windows XP professional if that matters, but nothing has really changed in it since I left using it. I still do the maintenance for it.

---

