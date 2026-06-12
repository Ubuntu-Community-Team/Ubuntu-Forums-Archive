---
title: "enable NTFS support, cant mount NTFS after today's updates"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by thespinesplitter on 2005-10-12
well today i restarted my system as usual since my mom refuses to use linux even though i set her up a nice and easy to use account with all the things she does, anyway

there where updates to be done so i updated my BREEZY PRERELEASE,
after doing that my GRUB went to hell so popped in the ubuntu instal cd got to manually edit partition tables pressed goback and chose instal grub bootloader then everything worked, windows finally booted once again but somehow my NTFS partition wouldntt mount 

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1      /mnt/windowsfiles ntfs ro,user,noauto,umask=0222 0 0
```

fdisk -l output
```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5839    46901736    7  HPFS/NTFS
/dev/hda2            5840        7233    11197305   83  Linux
/dev/hda3            7234        7297      514080    5  Extended
/dev/hda5            7234        7297      514048+  82  Linux swap / Solaris
```

i dont think its even trying to mount it at boot or else id get a failing module on boot, but i dont really know whats going on or how to check if thats the problem and start the module mannualy.

i read on a forum somewhere that maybe i had to enable NTFS support, but it was a forum for more advanced users so no one said how to go about enabling NTFS support.

also im not quite sure but i think that fdisk -l used to only say NTFS and not HPFS/NTFS.

thx in advance

---

### Post by thespinesplitter on 2005-10-12
im thinking it was the kernel update.... wow it seems all i do is fix linux, 5 hours into this still no solution

edit: i should also add the fact that my fstab didnt even have my NTFS entry after the kernel update, so i mannually entered it, im not sure if i missed something

---

### Post by thespinesplitter on 2005-10-12
bump! bump! bump!

---

### Post by thespinesplitter on 2005-10-12
so no one has any idea

---

### Post by SilentCacophony on 2005-10-12
Forgive me if this is obvious to you and doesn't apply, but the only things I can think of are these:

Did you perform a **sudo mount -a** after adding the entry in fstab?

Is */mnt/windowsfiles* really where you made the mount point originally? The */media* directory is the normal place to mount things in ubuntu.

Other than that, I don't know.

---

### Post by thespinesplitter on 2005-10-13
i made the mountpoint in /mnt, seemed like the right thing to do but it used to work like that, im going to try /media/windowsfiles

---

