---
title: "Starting up Edgy Eft 6.10"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by dolaksiz on 2007-05-18
Hi,

I had installed 6.10 one month ago onto an XP computer. There was no problem, and I was really happy with my Ubuntu. Then I formatted the C: drive and installed Vista (by deleting XP). I wasn't happy with Vista so again I installed XP :) Then I couldn't see the GRUB, and XP automatically started. So I followed the instructions and restored the GRUB by using Super Grub. Now I can see my old GRUB (with the default values and waiting times I had edited back when I used Ubuntu). But when I try tu login to Ubuntu it crashes. I tried to login with recovery mode and I get a message like:

can't access tty: job control turned off
(initramfs)

and a blinking cursor. I can write anything but it just does not accept them as command lines. CTRL+ALT+F1 (or F2, F3, etc..) does not work either.

I booted with the liveCD. In the terminal I enter,

sudo fdisk -l

and I get,

/dev/sda1   NTFS ... and continues something
/dev/sda2   W95 Ext'd (LBA)...
/dev/sda3   W95 FAT32...
/dev/sda5   Linux...
/dev/sda6   Linux Swap/Solaris.....

I can mount the sda5 by typing,

sudo mount /dev/sda5 /mnt

And I can see all my old files, but what should I change, I don't know.. I made all these by searching in the forum, but I couldn't find a solution.

What should I do?

---

### Post by starcraft.man on 2007-05-18
Wow, I'm gonna guess you made a pretty mess of your MBR with all those reinstalls and changes. Since you already tried the super grub repair and that failed, I see we need some more drastic measures. Luckily, it comes in the form of a great program. [GAG]("http://gag.sourceforge.net/") is my back up bootloader. It is a simple tool, basically it will search across your drives and put up to 9 different OS in the boot menu, its easy to use read documentation, download burn and boot into it. Then let it overwrite GRUB. If Ubuntu can be booted, this should let you do so. If after using this you still can't get to the log in screen, then I can only surmise that you overwrote something important and you should back up and then reinstall Ubuntu.

Best of luck, keep GAG close in future just in case. Oh and if GAG works, you can always restore a new GRUB from inside with the terminal of course :).

---

