---
title: "help with installing ntfs write on ubuntu"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by shaheel16 on 2008-01-26
here is the lists of drives:
shaheel@shaheel-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a0c4f45

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hda2            3188        4916    13888192+  83  Linux
/dev/hda3            4917        4998      658665    5  Extended
/dev/hda5            4917        4998      658633+  82  Linux swap / Solaris

what should I do so as to enable write to ntfs partition[hda1]?????

---

### Post by Presto123 on 2008-01-26
Does the NTFS drive show? What exactly do you need to write to it?

If you answered "yes" to the first q, then normally, you can do a typical file/folder/etc. and just move it to the drive and the location you want.

---

### Post by shaheel16 on 2008-01-26
yes the drive shows up.. I can browse through the files in the NTFS partition but i cant write to that ntfs disk... what should i do???

---

### Post by Presto123 on 2008-01-26
Are you wanting to write something like a document or take a picture and just copy it over to the drive? If you could help me out here with what kind of files, I might be able to help.

---

### Post by meindian523 on 2008-01-26
Are you using Ubuntu Feisty or Gutsy?

---

### Post by shaheel16 on 2008-01-26
thanks a lot.. but i fink it is working.. I restartted my computer and when i went to aplications--->systems tools---> ntfs...  it showed up my partiiton and i selected it for write purpose.. i hope this is enough and i dont need to configure other stuff??

---

