---
title: "X Crashes when I CTRL + ALT + F*...."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-01-14
WHen Ever I try to make a new X window whether with or without xgl, x crashes :(. Is there a way to fix this? Also Is there anyway to get DRI with XGL and an ATI x1600 card. Glxgears runs correctly with standard metacity + gnome, but not with xgl

---

### Post by fsando on 2007-01-14
Hi I have x1600 too - and have it working - have been through a LOT of pain the last two weeks.
My experience is that you should not go with newest drivers but use the ones in the repo (ie. install with synaptics). The new ones may be better but no one seems to know exactly how to set them up correctly - or perhaps they are not yet supported in ubuntu?
I now believe that most of my pain comes from not realizing that my system actually was at its current best. I tried to make it better ending up reinstalling.
I eventually followed this guide:
[COLOR="Blue"]_[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)_[/COLOR]
Which is working perfectly (i use the 'cutting edge' svn-beryl and it is great)
I've seen a lot of different settings recommended around the net - and in here. So now I'm testing it all systematically whenever I've got the time (today I tested 5 different recommendations for **/usr/bin/startxgl**. The one recommended in the above link was the only one that worked correctly.
EDIT:
btw this is what I get with fglrxinfo:```
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```
I've asked about the "XFree86-DRI" error and it is supposed to be that way - "ati-drivers do not support it under xgl" is the answer I get - I'm not sure what it means though :)

EDIT 2: The "XFree86-DRI" error does not occur in a non-xgl session.

---

### Post by fsando on 2007-01-14
One other thing:
I was given the following advice:
When the **splash**  option is part of the boot command the console screen (ie. ctrl+alt+F2) is completely unreadable. Solve this by editing the boot menu remove the **splash** and **quiet** from the boot command.
```
sudo gedit /boot/grub/menu.lst
```This might help another potential problem?

---

### Post by rj686 on 2007-01-14
Thanks for the help man. That is actually the guide i followed (guide worked perfectly) but overall I had almost the exact same issues as you :). For awhile I couldn't even get dri acceleration in standard but eventually it worked. I'm running 8.33.6 (compiled my own debs) and they work well.

---

### Post by fsando on 2007-01-15
You're welcome :)
> **rj686 said:**
> I'm running 8.33.6 (compiled my own debs) and they work well.
Could you explain to me how you did it?

---

### Post by Zaffe on 2007-01-15
Uhm.. if the problem its that you cant see the tty1 to tty6, add "vga=0x318" in the kernel load in /boot/grub/menu.lst
Example:
```
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash vga=0x318
```

---

### Post by mcduck on 2007-01-15
I fixed this problem by adding 'vga=792' to kernel options in Grub. It makes Ubuntu boot with 1024x768 resolution and 32bit colors, so GDM and VTs also use this setting. Gnome still runs with 1280x800. (I didn't need to disable usplash)

---

### Post by fsando on 2007-01-16
> **mcduck said:**
> I fixed this problem by adding 'vga=792' to kernel options in Grub. It makes Ubuntu boot with 1024x768 resolution and 32bit colors, so GDM and VTs also use this setting. Gnome still runs with 1280x800. (I didn't need to disable usplash)

They are the same 0x318 == 792.

I didn't work for me though, do any of you have a list of codes for different screen settings so I can test?

EDIT. Ha ha, it worked and it didn't (i put in as a quoted string - not a good thing). 
It still didn't work quite as expected. ttys are apparently fine. The splash, though, not so good. It is clearly readable but entirely misplaced, repeated and broke up and strechting beyond the monitor. Would still like a list of codes.

---

