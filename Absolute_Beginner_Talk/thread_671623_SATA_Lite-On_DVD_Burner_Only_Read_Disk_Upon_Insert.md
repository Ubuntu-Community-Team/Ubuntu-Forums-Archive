---
title: "SATA Lite-On DVD Burner Only Read Disk Upon Insertion"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by jeepfreak2002 on 2008-01-18
Well - here goes.  I have 2 identical SATA DVD Burners by Lite-On.  I have noticed that if I insert an audio CD the system can read the disk and it will ask me what I want to do, ie play the disk or extract.  If I ignore, and say go back and double click on the mounted disk later, it says that it is unable to read.  Amrock and Sound Juicer also are unable to read the disk after the initial insertion.  It's real weird.  I can play the disk once I insert it, but once I get out of the initial prompt message it is screwed.

here is the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3c09652e-58ec-4f30-ad17-8ffd06525b86 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9d592b5a-48bb-4a88-bd09-1ffbabb2ab39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


This is really annoying...  How can a system not read a standard SATA optical drive???

---

### Post by acormack on 2008-01-19
I don't think Audio CDs are ever mounted.

Only filesystems e.g. containing oggs or  mps3 files would mount therefore (I believe) fstab is irrelevant to your CDs.

What are you trying to do with the CDs?

---

### Post by jeepfreak2002 on 2008-01-19
I am simply trying to play them.  I stick the disk in, and if I play it right away, it will work.  If I decide to play it later, the disk is unable to be read.

---

### Post by c0met on 2008-01-19
Have you had a look in [COLOR="Purple"]Preferences >> Removeable Drives and Media[/COLOR]? It might be a setting in there.

---

