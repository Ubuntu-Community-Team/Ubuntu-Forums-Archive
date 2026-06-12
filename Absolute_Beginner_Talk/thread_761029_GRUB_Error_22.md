---
title: "GRUB Error 22"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by ajwest on 2008-04-20
I have 2 external WD hard drives.  I put in my Ubuntu live CD and then clicked "install."  I managed to install Ubuntu on 1 of these drives.

So this is what I've done.

My internal C drive has Windows installed on it.
My first external USB hard drive (my F drive) has 3 partitions.
   1: A large space.
   2: A 1 GB "Swap" partition. (I have no idea what that's for, but as far as I can tell it's required.)
   3: A 20 GB partition that I installed the Ubuntu OS on.


Anyway, everything appears to work fine.  I turn on my computer and it says to choose and OS, and then if I don't select anything it automatically goes into Windows. (I read on another forum how to change the default from Ubuntu to Windows.)

Ok, now since that first re-boot, whenever I turn off my computer and then back on again it says, "error 22."  From what I can tell, that's a problem loading GRUB because it can't find the HD that it's installed on.

When I go into my BIOS, my internal drive is selected to boot from first and then the two USB drives follow it.  The only way to boot into Windows or Ubuntu without the "error 22" message is to go into the BIOS and then exit it again. I assume that this is to give the USB HDs a chance to "Boot up" because when it first tries to load GRUB the HD hasn't started up all the way yet, there's a short delay.

Of course, if I don't have the HD plugged into the USB port at all, I would still like to have the option of loading Windows.  I don't want to have to bring an external hard drive with my laptop everywhere just to load an OS.

Any suggestions? Thanks for your help.

-AJ

---

### Post by tvtech on 2008-04-20
from the grub manual itself

22 :** "Must load Multiboot kernel before modules"**
This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.

when you installed ubuntu where did you install grub too?  the master drive in the computer or the external.  it sounds like you've written over your mbr for windows

you'll need to get into the windows boot file and do a fix [mbr]("http://pcsupport.about.com/od/termsf/p/fixmbr.htm")  gives a brief how too on how to do this in xp and 2k

p.s. SWAP  what it is.  linux is designed to run well on lower spec machines i.e. low ram.  swap is much like windows virtual paging file,  it uses hardrive space to cache non critical operations information.  the difference is, windows sticks it where ever it feels like it and you have no choice, you can't place it on the drive to optimize read times on it or anything so it's mostly useless.  in linux it's the same thing only it allocates a dedicated location on the drive for this area making it less of a pain for file operations in the rest of the system, and you never have to guess how much space you really have left.

---

### Post by ajwest on 2008-04-20
Wow, you're awesome. That fixed everything!

You're my hero.  You even explained what SWAP means!

Thanks tvtech!

---

