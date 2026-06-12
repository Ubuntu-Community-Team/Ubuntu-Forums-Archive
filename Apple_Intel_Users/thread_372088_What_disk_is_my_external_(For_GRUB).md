---
title: "What disk is my external? (For GRUB)"
date: 2007-02-27
forum: Apple Intel Users
---

### Post by neutrino15 on 2007-02-27
Hello,

I am trying to install ubuntu edgy to my firewire external disk.

I posted another thread here about that, but this is more specific..


Every time I try to install it, GRUB fails to install. When I go into the GRUB shell, and try to set it up there, almost all my commands have errors returned. (from invalid filesystem, to disk does not exist)...

In the gnome partition editor, I see that my main disk is sda and my external is sdb. My swap partition is 4, and my main (linux root w/ boot flag) is at 2. 

Grub will not install to hd0, sda, nor any of their partitions.


Where should I install grub?
Thanks!

---

### Post by oskarloko on 2007-03-06
It's (hd1,1)

You must setup and install it to this partition in order to work directly...

---

