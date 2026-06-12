---
title: "module loading/shell scripts for startup"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by madanglian on 2007-03-08
Hi,
I've been following the howto on using the Creative Labs DXR3 with GNU/Linux which is [here]("http://dxr3.sourceforge.net/howto.html") but come to a bit of a dead end on loading the kernel modules at startup.

Under the section "Loading the Kernel Modules", the Howto says I should be able to "issue the appropriate modprobe/insmod/rmmod commands by themselves and enter the module parameters on the command line or in /etc/modules.conf."

I couldn't find a file called modules.conf in /etc/, is there another way of doing this so that the kernel modules (em8300 and adv717x) can be loaded at bootup?

I also looked in /etc/init.d/ but that looks scary! With Debian policies and the like.

Also, every time I use the mknod commands (slightly further up the Howto), the nodes appear in /dev/, but when I restart my machine they are gone! Do I actually have to use them for them to gain a foothold or do they have to be recreated every time I boot?

Hope its ok to put these questions in the "Absolute Beginner Talk" section as my questions are (I hope) fairly basic and not directly related to Multimedia issues

Thanks!

Madanglian

---

### Post by lloyd_b on 2007-03-08
> Under the section "Loading the Kernel Modules", the Howto says I should be able to "issue the appropriate modprobe/insmod/rmmod commands by themselves and enter the module parameters on the command line or in /etc/modules.conf."

I couldn't find a file called modules.conf in /etc/, is there another way of doing this so that the kernel modules (em8300 and adv717x) can be loaded at bootup?

The file you want is "/etc/modules", not "/etc/modules.conf".  Just add lines for "em8300" and "adv717x".

> Also, every time I use the mknod commands (slightly further up the Howto), the nodes appear in /dev/, but when I restart my machine they are gone! Do I actually have to use them for them to gain a foothold or do they have to be recreated every time I boot?

In recent Linux kernels, "/dev" entries are no longer actually stored on disk.  Via the "udev" subsystem, this directory is basically a ram disk, and the entries in it are created by the kernel when the drivers for a particular device are loaded. 

Those entries *should* be created whenever the associated modules load.  The fact that this isn't happening makes me wonder if you're running obsolete versions of those drivers.

I suspect that there's some way to tell udev to create those entries when the system boots, but I haven't a clue as to what it is.  Hopefully somebody else will wander by with that info.

Lloyd B.

---

### Post by madanglian on 2007-03-11
Thanks for the reply. 

I looked in /etc/modules but there were only two simple entries there before I added ADV717x and em8300. I need to be able to pass parameters to the module such as "audio_driver=alsa". According to dmesg the modules have loaded but I still don't know if it has taken any notice of these parameters.

Also I still haven't been able to get udev to create the nodes in /dev/. Any ideas, anyone?

---

