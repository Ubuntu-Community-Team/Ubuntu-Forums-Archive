---
title: "Boot sequence just gives me blinking cursor , no grub"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by TimBilly on 2007-09-10
I just installed Linux for the first time yesterday (on my way to creating a MythTV box), but I'm getting a very odd blinking cursor screen. I've searched all of these forums for something similar, but it seems everyone else can at least get to GRUB.

I'm getting nothing. My computer BIOS does its thing, then straight into the blinking cursor. Not much to go on for troubleshooting at first glance. Ubuntu has it's own dedicated 160GB hard drive fresh out of the box. It is on a slave rather than a master, but I can't see that that would create a problem.

Here's the thing: it boots like a champ off of the LiveCD. Lemme go a little further, not only does it boot like a champ off the LiveCD, If I let the main screen load off the LiveCD (Start or install, Mem test, etc.) and select the last option, "Start off the hard drive first" or whatever, it goes to a black and white screen listing the Ubuntu install, Ubuntu (recovery mode), memtest, and my XP install on the old hard drive. I can select Ubuntu, and it fires right up off of the hard drive.

I can eject the LiveCD and continue on. It will even wake from hibernation using this sequence. What's happening in the boot sequence that's dumping me to the blinking cursor?

I'm writing this from FIrefox in Ubuntu, I don't really want to reformat the disk if I can get this install to work. I can post more info, but I have no idea what's relevant.

-------------
System specs (don't laugh):
Ubuntu 7.0.4
Athlon XP 1600+ (1.4Ghz)
ASUS A7N8X-?? (some old HP-WalMart special that doesn't show up on the ASUS web site)
WD Caviar SE 160GB
768 MB ram
Some old Maxtor HDD with a barely functioning XP install
nVidia GeForce FX 5200 (it was cheap)
Generic USB card
RT2500 type wireless ethernet controller
ATI HDTV Wonder card that I haven't played with yet in Ubuntu
Some other stuff that shouldn't matter

---

### Post by arai on 2007-09-10
[this solved]("http://ubuntuforums.org/showpost.php?p=3298265&postcount=10") the same problem for me. but i am not sure

---

### Post by Nulifier on 2007-09-13
Go into your dios settings and for boot sequence.
there should be an option for selecting which harddrive you want to boot from first

Because GRUB does not load it sounds as if you are booting off the wrong one so simply select the other HD (I assume that since this is the slave there is a master)

---

### Post by alienexplorers on 2007-09-13
If that did not work try booting from your Live-CD.
Enter terminal and type:
> sudo grub
> find /boot/grub/stage1                     Will produce an output such as (hd#,#)
> root (hd#,#)
setup (hd#)

quit grub and reboot

---

### Post by shendric on 2007-12-20
I'm having the same problem.  I've tried the grub instructions from alienexplorers, rebooted, and got nothing but the blinking cursor.

I'd really appreciate any help on this.

---

