---
title: "Reformatting windows partition for extra linux space on dual boot laptop"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by timgrin on 2007-10-08
I am going to reformat my ntfs windows partition on my dual boot laptop - I no longer need windows.

Windows is currently located at /dev/hda1 mounted at /media/hda1

I plan to format to ext3 using gparted.

Will i have a problem with grub bootloader - if yes what and how do I fix it?

This is my fdisk -lu

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    63713789    31856863+   7  HPFS/NTFS
/dev/hda2        63713790   152505044    44395627+  83  Linux
/dev/hda3       152505045   156296384     1895670   82  Linux swap / Solaris

Thanks ahead for any comments

---

### Post by Pumalite on 2007-10-08
You might; but if you do, just re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

