---
title: "Choice of kernel"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-07-28
Hello,
     When I had installed ubuntu 7.04 about 2 months back kernel 2.6.20.15 was installed from the CD. Later an upgrade was available , which I sincerely downloaded(2.6.20.16).

Now is a stage where both the kernel show up during bootup and leave the choice to me as to which one to use.
I have been using 2.6.20.15 till date. I am afraid that using the upgraded ver. may cause some problems if my configurations were not imported to it properly.
Someone please tell me how I can I have just one of the two displayed during bootup and how to  optimise it for better performance.
Thanks in advance.
:guitar:

---

### Post by gupta_sumesh63 on 2007-07-28
> **gupta_sumesh63 said:**
> Hello,
     When I had installed ubuntu 7.04 about 2 months back kernel 2.6.20.15 was installed from the CD. Later an upgrade was available , which I sincerely downloaded(2.6.20.16).

Now is a stage where both the kernel show up during bootup and leave the choice to me as to which one to use.
I have been using 2.6.20.15 till date. I am afraid that using the upgraded ver. may cause some problems if my configurations were not imported to it properly.
Someone please tell me how I can I have just one of the two displayed during bootup and how to  optimise it for better performance.
Thanks in advance.
:guitar: little knowledge about everything can be dangerous.....

---

### Post by shae on 2007-07-28
Next time you boot, use the new kernel.  You do not have to load any special configuration or anything.  After trying out the new kernel to make sure there is no problems with your hardware under it, you can remove the old version in synaptic.  Search the term linux in the name and remove the old packages.  If you need more help with that, please ask.

In terms of improving performance, the default kernel is optimized for desktop use, but if you really want to get every bit out of your hardware, you may consider compiling a custom kernel.  If you need help with this, ask.

However the fastest way to improve performance if you have less than 512 MB of ram is to add ram.  Ram is cheap now in most cases and can be had for less than 50$!

If you would like more tips to improve performance, I would like to know what experience level you have with linux so I may know what I can recommend.

Good luck,
Shae

---

### Post by yorkie on 2007-07-28
if you just want to display one kernel then type

sudo gedit/boot/grub/menu.lst
 brings up editor then you can  delete the one you don`t want or comment the lines out  the second option is handy if new kernel gives you problems you can change back to previos one easily
if you don`t know what comment out means simply put a  # in front of lines you don`t want displayed

---

### Post by carloslosgrande on 2007-07-28
You can keep the older kernel without causing any problems whatsoever, its kept by default in case of some difficulty with the new version.

---

