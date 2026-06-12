---
title: "Won't recognize slave"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by dustyken on 2007-04-18
I'm having a problem.  I backed up all of my important stuff on my slave, but Ubuntu won't recognize it.  Do I need to set it up differently?  Does it need to be formatted a certain way?  Also, I use xbmc on my xbox.  When I was running Windows XP, xbmc would recognize my network.  Do I need to set up a network in Ubuntu?  If you can't tell, I'm an absolute newbie.  Any help would be appreciated.  Thanks in advance.

---

### Post by taurus on 2007-04-18
What filesystem is your slave drive?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by dustyken on 2007-04-19
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       28006   224958163+   7  HPFS/NTFS
/dev/hda2           28007       30299    18418522+  83  Linux
/dev/hda3           30300       30401      819315    5  Extended
/dev/hda5           30300       30401      819283+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161    7  HPFS/NTFS

---

