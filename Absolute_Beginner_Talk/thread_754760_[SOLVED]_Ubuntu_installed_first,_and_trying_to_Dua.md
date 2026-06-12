---
title: "[SOLVED] Ubuntu installed first, and trying to Dual Boot WinXP"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Nerdriot on 2008-04-14
Hey all,

Ok, so here's my problem.

I've been using Ubuntu 7.10 only for a while, but until I get a new graphics card, I thought I would install XP on another partition, so I could play Guild Wars.

However, after going through NUMEROUS WinXP installation-related problems, I decided I would boot into Ubuntu and look up some help for the WinXP side. However, WinXP has taken over as the "booting OS", and my GRUB menu doesn't come up anymore.

I booted a Ubuntu live cd, went into GParted, and selected the ext3 partition with Ubuntu as the booting OS, and now, when I turn the computer on, it said, "Error finding operating system."

I have no idea what to do now. I'm writing you right now through the live cd.

Any help is greatly appreciated!

---

### Post by Nerdriot on 2008-04-14
Nevermind, figured it out.

Ran GParted through Live CD, changed XP out of "boot", and made Ubuntu "boot".

Then, I ran "sudo grub", then "find /boot/grub/stage1". Then, "root (hd0,0)", then, to set up GRUB as the bootloader, I ran "setup (hd0)".

All is well again.

---

