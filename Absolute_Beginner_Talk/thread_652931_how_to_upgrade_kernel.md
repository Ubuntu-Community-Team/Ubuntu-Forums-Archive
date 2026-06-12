---
title: "how to upgrade kernel"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by stunningman on 2007-12-29
can anybody tell me how to upgrade kernel and what is the benefit of upgrading.

---

### Post by Kosimo on 2007-12-29
You shouldn't do this (otherwise you really know what you're doing)

Ubuntu gives us in every release the latest *stable kernel.  I strongly recommend you to keep using the current one since Herdy comes with the newest one.

Why would you like to update it?

---

### Post by Flyingjester on 2007-12-29
I agree with Kosimo, upgrading the kernel is kind of hit or miss, you may end up with an incredibly unstable kernel.

---

### Post by aktiwers on 2007-12-29
The easiest way I found was to use KernelCheck
[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

Just remember that when upgrading the Kernel you need to reinstall lots of drivers. Also you could be put in a state where you cant boot the Kernel, then you need to hit ESC before GRUB loads and pick a older kernel. 

Then you should probably go to your menu.list and remove the unfunktional kernel and maybe delete it from your computer manually.

But as suggested, maybe you should not do this. Though it can increase speed of the computer, or give you better support for some hardware.

---

