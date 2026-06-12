---
title: "Grub boot loader gives too many choices after update?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-03-13
I just did an automatic update and this included
an updat4e of the linux image.  But now in
6h4 grub boot loader I have a choice between
two kernels:
2.6.17.11 generic
2.7.17.10 generic

I'm confused by this and this is my wife's
computer and there should be no confusions
for her because I am trying to convince her of
the wonders of linux over windows.

If I did an automatic update why is the older
version still offered as a choice?   Do I need
to worry about something?

Thank you,
Michl

---

### Post by Skidpad on 2007-03-13
No you don't need to worry, mine did the same thing when I upgraded.  You can handle this a couple of different ways: 

1) Edit your Grub menu.list file and "comment out" (place a # sign in front of) the lines referring to your old kernel.  This will cause Grub to overlook and not display these in the boot menu.  This is easy to do:  sudo gedit /boot/grub/menu.lst

Here's mine, notice the **#** in front of the 2.6.17-10 lines

==============================================
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

**#title		Ubuntu, kernel 2.6.17-10-generic**
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

**#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)**
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

==================================================

or:  2) Remove the old kernel.   

I'll leave the experts to chime for details/pros/cons on #2  :)

---

### Post by Michl on 2007-03-14
Thank you!  Just saw my menu.lst.  So following
strategy 1, I would just comment out the "title"
line, not the following lines between 'root' and
'boot;.

I will wait to see if there are any comments about
removing the old kernel.  That was my initial thought,
but got nervous.  Everything is running smoothly right
now.

M

---

### Post by AtrejuT on 2007-03-14
in my experience, when you tried the new kernel and everything is working it is quite safe to remove the old one. you should not do that without booting into the new kernel first to confirm everything is working, though!

some people like to keep the second-oldest kernel around, in case something happens to the one they use. I don't, but I guess thats just a matter of taste.

atreju

---

### Post by Skidpad on 2007-03-17
> **Michl said:**
> Thank you!  Just saw my menu.lst.  So following
strategy 1, I would just comment out the "title"
line, not the following lines between 'root' and
'boot;.
M

Exactly.  The # symbols on the **bold** lines in my post above are all I added to keep the old kernel from appearing in my Grub/menu list during boot.

During the last couple of days, there have been other threads about removing the old kernel via Synaptic also.

---

### Post by bapoumba on 2007-03-17
The proper way to remove an entry in grub menu is to remove the kernel (from synaptic, it's okay).
Commenting in grub is only a temporary fix, as the menu gets overwritten every time there is a kernel update or a kernel removed. So next upgrade, you will have to do it all over again.

In addition, I always recommend to keep the previous kernel. If anything goes wrong with an update, you can always boot with the previous kernel.

In /boot/grub/menu.lst, check these two lines:
```
default         0
timeout         10
```
default is the default kernel to boot, ie the first one in menu.lst.
timeout gives the number of second to wait before to boot on the default kernel.
So here, I have 10 secs to choose another kernel to boot from, which  is enough, and not to long to wait for the default boot, without doing anything.

---

### Post by Skidpad on 2007-03-17
^^^^^ I understand bapoumba.  I had planned to remove the old kernel prior to the next update.  As you stated, my fix was temporary until I learned more about the proper way to complete kernel removal.

Thanks for the info!

---

### Post by bapoumba on 2007-03-17
You're welcome :)
> **bapoumba said:**
> 
In addition, I always recommend to keep the previous kernel. If anything goes wrong with an update, you can always boot with the previous kernel.

> **Skidpad said:**
>  I had planned to remove the old kernel prior to the next update.  As you stated, my fix was temporary until I learned more about the proper way to complete kernel removal.

May I stress again keeping the previous kernel ?

---

### Post by Michl on 2007-03-18
> **bapoumba said:**
> 

May I stress again keeping the previous kernel ?

bien sur ... I have kept everything as is and it does not
bother my wife.  She just waits for it to boot automatically
and ignores the other stuff.  The last line in the menu is for
the Windows os and so it is easy for her to get down to
that when she needs it.

So far I see no differences running the newer kernel.

Michl

---

### Post by Mateo on 2007-03-19
> **bapoumba said:**
> You're welcome :)


May I stress again keeping the previous kernel ?

Waste of hard drive space.

---

### Post by Dark Lord Peaches on 2007-03-21
im having the same deal with the different kernels showing up, how would i go about uninstalling the older kernels

---

### Post by undertakingyou on 2007-03-21
> **AtrejuT said:**
> in my experience, when you tried the new kernel and everything is working it is quite safe to remove the old one. you should not do that without booting into the new kernel first to confirm everything is working, though!

some people like to keep the second-oldest kernel around, in case something happens to the one they use. I don't, but I guess thats just a matter of taste.

atreju

I do the same thing on some of my machines when I don't want to recompile and install modules.

---

