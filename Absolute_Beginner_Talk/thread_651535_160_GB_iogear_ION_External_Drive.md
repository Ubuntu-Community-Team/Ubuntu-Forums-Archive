---
title: "160 GB iogear ION External Drive"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by g45model21 on 2007-12-27
I have an old Iogear 160GB ION Drive that I was using with windows.  Ubuntu sees it, but it says it can't mount the drive because it us read only.  How do I get to be able to use it?  I am a severe newbe at linux.

---

### Post by yamfox on 2007-12-27
To fix the problem System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

---

### Post by g45model21 on 2007-12-31
Thank you

What will this do and what to do after I do this?

---

### Post by taurus on 2007-12-31
What is the filesystem, ntfs or fat32, is your external harddrive?  If not sure, post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L, not number 1.

---

### Post by g45model21 on 2008-01-01
File System:  HPFS/NTFS

---

### Post by taurus on 2008-01-01
Can you post the outputs of these commands?

```
sudo fdisk -l
mount
```

---

### Post by g45model21 on 2008-06-01
> **taurus said:**
> Can you post the outputs of these commands?

```
sudo fdisk -l
mount
```

sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x513a5139

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris
lakes@lakes-desktop:~$ 

mount

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x513a5139

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris
lakes@lakes-desktop:~$

---

