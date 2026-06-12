---
title: "What needs to be done after using Envy to install Nvidia driver"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by davexnet on 2007-12-31
Hello, I have the Nvidia Geforce 6100 intergrated on my mobo chipset.

The download, install & running of envy seemed to work, but something wasn't right.
For example, open windows would dim and brighten at odd times, flashes when the pointer
was placed in the top action bar.  Also, if using the pointer to drag a window corner
to enlarge/shrink a window, the window would turn an odd dark color.
Occasional sluggish desktop navigation.  Something wasn't right.

All this started after a recent kernel update; I ended up uninstalling the Nvidia
driver and envy and reinstalling.  As I mentioned it was successful(as far as I could see)
but something, somewhere was amiss.

I tried a bunch of thngs, but eventually, system/administration/screens and graphics
and setting nvidia in the graphics card/driver section seemed to fix the obvious problems
I could see.

I thought NOTHING further had to be set if envy was used.  As well as applications/
system tools/nvidia settings, there is also system/preferences/screen resolution,
and the system/applications/screens and graphics mentioned above. For example,
the refresh rate in system/preferences/screen resolution is different than the one in
nvidia settings.  How do all these things work together.  It;'s very confusing for a
newbie.
Dave

---

### Post by SOULRiDER on 2007-12-31
Type this in a terminal. If the output is **Driver "nv"** it means youre not using the nvidia drivers, if it is  **Driver "nvidia"** it means youre already using them and nothing needs to be done.
```
cat /etc/X11/xorg.conf | grep Driver
```
(you may get some other lines, but just look for one of those two)

Paste the results and we'll see what has to be done.

---

### Post by davexnet on 2007-12-31
Hello, this is the output:
davexnet@davexnet-desktop:~$ cat /etc/X11/xorg.conf | grep Driver
    Driver         "kbd"
    Driver         "mouse"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "nvidia"

I'm using the driver ? It seems as if I am now because, the desktop navigation is
snappier, the colors look right and no anomalies when moving / resizing windows.

The problem is, it wasn't right after the envy/driver reinstall - I did something to get here,
not sure what, I did a lot of things, various commands I'd seen in the forum, not sure what fixed it.

What should you have to do after this reinstall.  I'm concerned because it seems as if it will be necessary upon certain Ubuntu (kernel related?) updates.

Dave
PS the recent kernel update also screwed up my Grub menu.lst.
I had to manually edit it (as I did after Ubuntu was first installed.)  For some reason,
my SATA bootdisk and IDE secondary is throwing it out.  I had to change all references
(hd1,9) to (hd0,( to get it to work.  (see below)  _ I didn't touch the MAP commands
at the bottom.  Not really sure what is going on here either, why Ubuntu can't get it
right, or why a kernel update should modify this file at all.


to title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a0097fe7-5e27-44d5-9a79-cdc2ae1323a5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a0097fe7-5e27-44d5-9a79-cdc2ae1323a5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,9)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by davexnet on 2008-01-01
well I thought it was setup properly.  I finally put my glasses on, and saw the
tell-sign of an LCD at a non-native res.
I used the monitor "info" button and it revealed the current res at 1280* ????.
I finally got it working (after a reboot) at it's native 1650* ???? res.

Frankly, I'm amazed it worked, I didn't recognize anything in my attempt to change it
as an indication of success.

I firmly believe that as I get to know Linux a little better, these (seemingly) weird an wonderful
methods will make more sense.


Dave

---

