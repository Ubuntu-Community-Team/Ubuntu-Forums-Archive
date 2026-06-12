---
title: "Windows partition unreadable"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by hermitt on 2008-03-17
Hey,
So im trying to make a dual-bootable gutsygibbon and vista (i know, i know) machine, and i went though the ubuntu install process fine, using the built in partitioning device, to give myself 50 gb on my vista, 15 gb on ubuntu, a 6 gb recovery partition (is this necessary?  its a sony, and it came with the computer...but i don't really want it...), and whatever else the installation process added. 

the ubuntu installation worked perfectly, and i played around with it, and decided to resize everything and just use vista for emergencies...

however, when i tried to boot back into vista for the first time after the installation, the boot manager gave two options, both named the same for vista.  the first seems to be the boot-recovery manager, and the second seems to be the actually os.  the recovery part works fine (i did a few scans in that, no problems with hard drive or any other part), but when i try to boot into the second one, i just get a black screen with "starting up..." written on it, and it hangs without ever starting up vista.

i went into gpartition, and the 50 gb vista partition is now unreadable, with no data appearing, and no options available.

any help?  im decent with computers, but know very little about linux.

Thanks

---

### Post by NightwishFan on 2008-03-17
Well let us see what your disk looks like. Open a terminal and type:
```
sudo fdisk -l
```

---

### Post by hermitt on 2008-03-17
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2984b9a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6680576   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         833        7461    53247442+   7  HPFS/NTFS
/dev/sda3            7462        9628    17406427+  83  Linux
/dev/sda4            9629        9729      811282+   5  Extended
/dev/sda5            9629        9729      811251   82  Linux swap / Solaris

---

### Post by weezy8802 on 2008-03-17
well i would recommend reformatting and reinstall vista (assuming you back it up) resize vistas partition (google resize vista partition). then reinstall ubuntu using the guided free space option.

---

