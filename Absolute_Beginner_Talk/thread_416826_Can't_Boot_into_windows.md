---
title: "Can't Boot into windows"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2007-04-21
I've just build a new system...ASUS dual core 64 bit etc.....and was having problems getting GRUB to come up. After installing Ubuntu (dual boot with XP), when I restarted GRUB just wouldn't come up and it'd boot into XP as if GRUB didn't even exist. Anyway, I decided to try installing another distro...just to see if I got the same result. I tried Mepis. GRUB did come up on reboot after install...but I got the error 22 messages. Anyway, I tried installing ubuntu again, and joy of joys, GRUB came up this time. But the paths are incorrect.

The path for ubuntu come up as (hd1,2), but it is in fact (hd0,2).

Anyway, changed that no problem.

The thing is my XP paths are wrong too but I'm not sure what to try.

I currently have a SATA drive 

01 /dev/hdi1   Active (NTFS)
02 /dev/hdi2   linux-swap
03 /dev/hdi3   ext3 (ROOT)

Plus a PATA drive

/dev/hdc1   Fat 32
/dev/hdc2   extended

Basically my SATA drive if my OS drives, with XP installed on hdi1 and Ubuntu on /dev/hdi3.

Currently, in GRUB, the XP path reads as 1,0. I've tried 0,0, 0,1, 0,2....etc etc to try and guess but to no avail. What path would I have to follow to boot into XP again?


Kind regards....mel

---

### Post by Pobega on 2007-04-21
Try this in your menu.lst:

> title           Windows XP <your> Edition
root           (hd0,0)
chainloader+1
savedefault/boot (Whichever works for you)

---

### Post by SpongeBob SquarePants on 2007-04-21
Thanks Pobega....worked a treat :)

---

