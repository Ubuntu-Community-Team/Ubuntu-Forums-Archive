---
title: "replacing mobo needs format?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by fire_storm on 2007-05-24
I plan to replace my motherboard with a GA-p965-DS3 and different ram, do i need to reinstall the OS?


Thank you

---

### Post by igknighted on 2007-05-24
> **fire_storm said:**
> I plan to replace my motherboard with a GA-p965-DS3 and different ram, do i need to reinstall the OS?


Thank you

You could try to leave it and hope it reconfigures.  Some stuff may need to be reconfigured manually though.  The easiest way would be a reformat.

---

### Post by djheadley on 2007-05-24
I am running an hp pavilion, 1ghz, 256mb ram.   Now, that is.  I was running a 400mhz celeron machine and transferred all my drives over so it was essentially a mobo transplant.  You might have to reconfig xorg unless you're using the same video card.  That's all I had to do, anyway.

---

### Post by hartz on 2007-05-24
You should not need to reformat or re-install anything.

Particularly if you are using UUIDs for mounting file systems, which is the default in Feisty, can't remember what was the default in 6.10.  

You need to be careful of two things:  Firstly the GRUB menu might change, so you might need to fix it after installing the new motherboard.  This is because the GRUB menu depends on the order in which disks are seen.  Typically with only one hard drive in a machine, no change needs to be made.

If you have two hard drives, Grub might start to see another hard drive first and then try to boot off of that drive, and will fail.  This is not as big a problem as it sounds.

In the grub menu config file, hard drive and partition's are referred to by names like (hd[COLOR="Red"]0[/COLOR],1)
It is possible that the first number change, eg from a [COLOR="Red"]0[/COLOR] to a [COLOR="Blue"]1[/COLOR], depending on your hardware config.

At any rate, having a LiveCD handy in case you need to get back into the system that way is sometimes useful.

The other thing which could change is your graphics, particularly if you are using onboard graphics and have some restricted (i.e vendor supplied) drivers in use.

In that case, after the motherboard replacement you are likely to be left with command-line access only, eg no GUI.  If that it the case, run this command:
```
sudo dpkg-reconfigure xserver-xorg
```
That should reset drivers, etc.  Then run this command
```
/etc/init.d/gdm start
```
(Assuming Ubuntu/Gnome, substitute kdm if you are using KDE)

And then you should have everything back to normal.

To be sure, please show the output of these two commands before you start your upgrade:
```
cat /etc/fstab
uname -a
```

The fstab should use UUIDs for all file systems being mounted.

---

