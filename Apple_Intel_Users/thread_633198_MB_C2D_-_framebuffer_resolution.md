---
title: "MB C2D - framebuffer resolution"
date: 2007-12-06
forum: Apple Intel Users
---

### Post by Dale Cooper on 2007-12-06
Hi all,

I'm desperately trying to find a way to have a decent resolution for my framebuffer.

With my PCs i used to add something like "verbose vga=791" to my menu.lst, which has always worked great.

With the MB I only get a blank screen with this option.
If I uninstall usplash and leave default options in Grub I get my desired verbose bootscreen but the framebuffer is in 800x600 which is very ugly and quite unusable to work on the console...
I know that Grub cannot handle wide resolutions, but 1024x768 would be perfect.
All solutions I've found so far are for MBP with an ATI card.

Is there anyone out there who have already fixed this?

Cheers
Ben

---

### Post by cyberdork33 on 2007-12-06
there is a table of vga values here:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap1)


You can get the verbose boot output by taking of the 'quiet' and 'silent' options off the kernel line.

---

### Post by Dale Cooper on 2007-12-07
Thank you for the help, but it does not work.
As soon as put I anything like vga=xxx or vga=0x000 I got a blank screen.
I've also tried to use the intelfb driver at boot time with no better results.
I'll try to investigate a bit more.

The tip to remove the quiet and silent options works well though, thanks ;)

---

