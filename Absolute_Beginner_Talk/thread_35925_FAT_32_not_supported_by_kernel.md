---
title: "FAT 32 not supported by kernel"
date: 2005-05-20
forum: Absolute Beginner Talk
---

### Post by animesh on 2005-05-20
hi
   my XP drives fs was NTFS ,i converted it to FAT 32 with the help of partition magic and also changed the /etc/fstab file .Now on booting it says "FAT 32 not supported by kernel" and on opening windows drives when in ubuntu it shows c,d,e but nothing inside them ,whereas in windows there is no problem.
                                          plz suggest to do the needful ,thanks for ur support

---

### Post by Kyral on 2005-05-20
Okay, I knwo for a fact that FAT32 is supported in the kernel, b/c my anime HD is in FAT32.  Maybe PM did something funky, b/c as far as I know, converting one FS to another is kinda sketchy. You should have just left it as NTFS because Linux can read NTFS just fine.

Also what are the Mountpoints of "C: D: E:" because Linux doesn't refence drives that way (its more like /mnt/drive or /media/drive or /dev/hda)

Also, have you tried mounting them?

---

### Post by fng on 2005-05-21
Pasting the /etc/fstab file could always be handy for solving this problem

---

### Post by animesh on 2005-05-23
should i compile my kernel? 

here is my /etc/fstab file


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs defaults        0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /windows/c      FAT32   defaults,umask=0 0 0
/dev/hda5       /windows/d      FAT32  defaults,umask=0 0 0
/dev/hda6       /windows/e      FAT32   defaults,umask=0 0 0

---

### Post by hazza96 on 2005-05-23
[QUOTE=animesh]should i compile my kernel?[/QUOTE]
No, there is no need to.

[QUOTE=animesh]here is my /etc/fstab file
/dev/hda1       /windows/c      FAT32   defaults,umask=0 0 0
/dev/hda5       /windows/d      FAT32  defaults,umask=0 0 0
/dev/hda6       /windows/e      FAT32   defaults,umask=0 0 0[/QUOTE]
Shouldn't they be:

/dev/hda1       /windows/c      **vfat**   defaults,umask=0 0 0
/dev/hda5      /wi..... etc

---

### Post by animesh on 2005-05-23
thanks very much ,it worked. actually i am a newbie to linux as well as comp. fundaes

---

