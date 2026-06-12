---
title: "boot image name"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by michaelbesselman on 2007-08-24
I’ve decided to load Ubuntu, given your recommendation.  I have a special need though.  I need to specify mem=256M on the boot command line because my soldered-in memory is corrupt above 256M.  Typing just “mem=256M” alone does not do it because it is expected a boot image name first.  But I don’t know what the boot image name is.  Is there a general Linux way to get a list of boot images when I get the “boot:” option on startup?  Or is there a general name for the boot image that would normally be used if I just typed CR at “boot:”?

---

### Post by wormser on 2007-08-24
I am no expert in this area but I believe that the boot images are stored in /boot.  Look for files like initrd.img-2.6.20-15-generic.  The name changes with each version upgrade.

---

