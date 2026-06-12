---
title: "Changing ownership of files in a FAT partition"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-01-04
I have 2Gb FAT partition in my system, which is shared between Windows and Ubuntu. 

The thing is, the owner of all the files in the partition is the root, and I want the user to be the owner. 
```
sudo chown -R $USER:$USER name_of_directory
```
results in an error, and the same error even if I am logged in as root. 

Does that mean files on a fat partition can only be accessed by the root?

---

### Post by canadianwriterman on 2006-01-04
Can you post your fstab file? My entry for the fat32 partition is as follows and I have no problems with permissions:

/dev/hda2	/media/Shared	vfat	umask=000	0	0

---

### Post by harisund on 2006-01-04
/dev/hda7       /common         vfat    defaults        0       0

Well, the thing is, the $USER has all access previledges, as in I can create, browse and delete stuff. Just that the owner doesn't seem to be something that can be changed.

---

### Post by canadianwriterman on 2006-01-04
[QUOTE=harisund]/dev/hda7       /common         vfat    defaults        0       0

Well, the thing is, the $USER has all access previledges, as in I can create, browse and delete stuff. Just that the owner doesn't seem to be something that can be changed.[/QUOTE]

Okay, your entry in fstab doesn't look right. If you created your mount point in the /media directory like you should have, the line should read:

/dev/hda7       /media/common         vfat    defaults        0       0

---

### Post by aysiu on 2006-01-04
*defaults* means only root can read the files.
See the fourth link of my sig.

---

### Post by piedamaro on 2006-01-04
You need something like:
defaults,uid=1000,gid=1000

vfat doesn't have real file permissions, permissions are assigned at mount time.

---

