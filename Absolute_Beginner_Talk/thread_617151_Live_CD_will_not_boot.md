---
title: "Live CD will not boot"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by zephyrus17 on 2007-11-19
I have downloaded the 7.10 for my AMD64, many times. But it will not boot. Even after reformatting the DVD-RW, or reformatting windows, it will not detect the boot. Sometimes, it will, but I don't really know what's causing it.

I have checked md5sum, and I don't know how to do the verify CD thing.
Am I required to activate the wubi-cdboot first?

---

### Post by Sef on 2007-11-19
> I don't know how to do the verify CD thing.

Instead of going into the Live CD, go down the menu till you get to "verify cd" or something similar.

---

### Post by Mike Armstrong on 2007-11-19
I find it is best to burn the iso to a CDR at the lowest possible speed I couldn't get it to work with DVD RW.

---

### Post by tybalt on 2007-11-19
Hi,
I had the same issue with the previous versions of Live CD, but not with the 7.10 version.

With those versions where the LiveCD was unable to boot, i had to launch the LiveCD with the following commands included in the boot sequence:
vga=771 noapic nolapic

Hope this helps.

---

### Post by Arthur Archnix on 2007-11-19
This link might be helpful: [http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by bumanie on 2007-11-19
Are you sure your bios is set to boot from cdrom? Might be worth checking just to make sure.

---

