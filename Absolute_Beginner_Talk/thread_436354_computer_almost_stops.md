---
title: "computer almost stops?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by linuxhippy on 2007-05-07
I have Ubuntu 7.04 installed on my AMD Athlon 64 box using the 64 bit distro.  I've used Fedora Core 64 bit on this pc for years and have found that 1 application does not noticeably slow down my computer's performance.  Ubuntu does at times (for instance if I do a kernel compile the mouse is slow and almost unresponsive during the kernel build).  My pc almost stopping is not because of my hardware...what do I need to do to get Ubuntu to be more snappy?

---

### Post by jfinkels on 2007-05-08
More RAM? 64 bit processors can address up to 16 exabytes :D

---

### Post by jiminycricket on 2007-05-08
Perhaps try disabling acpi as a boot-time option and see if it improves.

---

### Post by linuxhippy on 2007-05-09
RAM?  I only have 512 MB that's shared by integrated video.  Not much, but it's been enough for Fedora Core for almost 2 years.  I am using different desktops, though.  In Ubuntu I'm using gnome desktop and in Fedora I'm using xfce.  KDE desktop eats up a lot of memory-is gnome desktop the same way?

I don't think acpi is enabled in /boot/grub/menu.1st and I use this:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,13)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b78f9ca4-cbc0-40da-8bee-87cfa49020ff ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

---

### Post by linuxhippy on 2007-05-09
it appears that 512 MB of RAM is not enough in GNOME desktop if multiple programs are running.  I installed XFCE desktop (sudo aptitude install xubuntu-desktop) and now my pc is snappy during a kernel build!!

Thanks for the help!

---

### Post by linuxhippy on 2007-05-12
I was wrong...xfce didn't solve my memory problem-though it did help.  I have the xfce cpu/memory meter installed on both Fedora and Ubuntu.  In Ubuntu when the CPU goes up the memory fills and the pc gets sluggish.  In Fedora when the CPU goes up the memory meter only fills to 271 of of 371 MB of phys RAM way doing the same tasks of kernel building and surfing the web with Firefox and 5 pages are open.  My video card is integrated and takes 128 MB of my 512 MB of RAM.  

Why the memory management difference?

---

