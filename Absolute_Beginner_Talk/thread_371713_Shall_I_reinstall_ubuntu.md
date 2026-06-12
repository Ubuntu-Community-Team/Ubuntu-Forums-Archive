---
title: "Shall I reinstall ubuntu?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by addisor on 2007-02-27
Hi guys, recently had Beryl on my edgy set up. Think it caused my virtual console access to stop, so I removed it, still no ctrl alt f1-6 at all. I really need this to work, shall i go for a reinstall of the O/S????

I have tried a few simple fixes from posts, but no fix.

---

### Post by Foudre on 2007-02-27
why not just turn beryl off? when you do something that makes it mess up, i love beryl, but i have to turn it off if i use anything opengl

---

### Post by MkfIbK7a on 2007-02-27
> **Foudre said:**
> why not just turn beryl off? when you do something that makes it mess up, i love beryl, but i have to turn it off if i use anything opengl

he no longer has beryl....

reinstalling is pretty extreme but if you have no files needed...

---

### Post by kinematic on 2007-02-27
take a look at /etc/inittab and see if anything at respawn:/sbin/getty is commented out.
you should see this at the end of the file:
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6
(i commented out getty 4,5 and 6....yours shouldn't be)

---

### Post by addisor on 2007-02-27
This is my inittab, what do you think?


# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

---

### Post by kinematic on 2007-02-27
that looks fine.
try this.
> sudo gedit /boot/grub/menu.lst
find #kopt= and add vga=0x318 (kopt means kernel option)
then do
> sudo update-grub
reboot and see if you can access it now.

---

### Post by addisor on 2007-02-27
i added that kopt as suggested, thought i'd post befor grub update in case i crash!!!

# default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=565540eb-bdaf-4de8-b3c1-991117c5d964-vga=0x318 ro

---

### Post by addisor on 2007-02-27
Total crash!!! stuck in grub, where to go now, just back to o/s would be great.

---

### Post by kpkeerthi on 2007-02-27
See if you can boot into recovery mode from grub menu. And then you can restore your menu.lst file. Oh btw... did you backup your menu.lst before you made that change.

If you are unable to boot into recovery mode from grub, pop in your live CD and choose 'Boot from hard disk' (something like that) and see if you can get into ubuntu and then back up you menu.lst

---

### Post by kinematic on 2007-02-27
> **addisor said:**
>  
# kopt=root=UUID=565540eb-bdaf-4de8-b3c1-991117c5d964-vga=0x318 ro

here's the problem.
you have 991117c5d964-vga=0x318.
there should be a space between that last line of numbers and vga=0x318 and no dash before vga=0x318!
you've tried to append an invalid number to the user id number...that's why you crash.
when you see grub press "c" for a command line...that will allow you to change the kernel line to boot.
when you're in ubuntu you can change grub permanently.

---

### Post by addisor on 2007-02-27
Cheers, managed to access grub, edited my primary kernel line and removed the offending letters, then booted as normal, edited my menu.lst and updated grub. All ok thanks. Why didn't mode work or did i put it in the wrong place???

---

### Post by picpak on 2007-02-27
What's your video card? Some (like mine) don't support the vga= option.

---

### Post by kinematic on 2007-02-27
that mode should work fine....that adjusts the kernel frame buffer wich can sometimes be screwed up by beryl.
the problem is that you tried to append vga=0x318 to the user id number.
just put a space and no dash between that line of numbers i was talking about and vga=0x318.

---

### Post by addisor on 2007-02-28
It now looks like this, but no change on ctrl alt f1-6, just my grub font has shrunk to tiny!!! boots ok.
# kopt=root=UUID=565540eb-bdaf-4de8-b3c1-991117c5d964 vga=0x318 ro
Any more console ideas? or is it reinstall time? trying to set up twinview so really need access to console.

---

### Post by kinematic on 2007-02-28
no....i'm out of ideas :-?

---

