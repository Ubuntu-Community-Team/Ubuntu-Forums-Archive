---
title: "WinXP and Ubuntu dual-boot with GRUB"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Daevius on 2007-06-23
Hi,

Alright, I thought to make a new thread of this one instead of replying the old one, with the wrong title...

I want to dualboot my computer with Windows XP and Ubuntu. I have two physical harddrives, one slave (XP) and one master (ubuntu, reinstallable). I tried to do this with windows's bootloader. But the 512kB bootsect.lnx was probably incorrect, as when I select it when booting it gives me a bleep and restarts.

So I thought it would be nice to use GRUB instead. However, I cannot boot into Ubuntu, as the win bootloader does not (described above) and when I change the jumper to the other harddrive, it says: DISC FAILURE and some more warning words.

I _can_ boot with the Live CD ofcourse, but what should I change that it will load GRUB or even Ubuntu?

PS: What does the migration assistant do/mean when you install Ubuntu?

Thanks in advance,

Daevius

---

### Post by Daevius on 2007-06-23
Well, I figured it out. Its working now. I just played with the jumper on the harddrive and with the BIOS, and suddenly it worked!

So, problem fixed :D

Daevius

---

### Post by mosaic2s on 2007-06-23
CMOS settings to select boot option works when you have 2 hard disks.

---

