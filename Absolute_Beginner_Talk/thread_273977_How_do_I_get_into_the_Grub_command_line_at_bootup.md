---
title: "How do I get into the Grub command line at bootup?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-10-09
My machine was dual booting Ubuntu and WinXP, until I deleted the XP partition (need to reinstall that from scratch.)

Now, I get error 22 (partition not found, I beleive) when booting up.  It took me a while to figure out how to get Grub set up in the first place, and I'm not sure what to do now.

I don't know how to get to the menu.lst in my install from the live cd, and I don't remember how to get into the Grub command line after the error at bootup. 

I think if I can get into the command line I'll be able to poke around and figure out how to fix it.

Any advice would be appreciated.

---

### Post by Charles Hand on 2006-10-09
Look at this thread: [http://www.ubuntuforums.org/showthread.php?t=267905](http://www.ubuntuforums.org/showthread.php?t=267905)

If you can't remember your root partition, try

fdisk -l /dev/sda
fdisk -l /dev/sdb
fdisk -l /dev/hda
fdisk -l /dev/hdb
...

look for large partition with Id 83.

---

