---
title: "mounting HD volumes"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-29
is it normal for the folder that represents a mount point for a volume to disappear every time the volume is unmounted?  for example if my volume mounts to /media/disk, i would be referring to the 'disk' folder under the '/media' directory.  when the volume is not mounted, the folder is not there, when it is mounted it shows up.  is this normal?  i created the volume under GParted and this is where the volume mounts to.

---

### Post by jeffus_il on 2008-01-29
Yes it is, I assume these are external disks which are not listed in the fstab file.

---

### Post by dgray_from_dc on 2008-01-29
I think it is normal.  What type of volume is it?  USB, IDE, SATA?

With most of these, especially external drives, I've noticed that mountpoints like disk, disk2, etc. appear and disappear.

Before, you'd get things like /media/sda1, /media/sdc2, etc. and sometimes they'd go away, sometimes they wouldn't.

If this is something you're experiencing with an internal disk, you may consider adding it to /etc/fstab for permanence.

---

### Post by Matt26 on 2008-01-29
the volumes are on an internal IDE hard drive, and i have tried adding then to /etc/fstab so i could have them mount automatically when the system start, but that didn't seem to work, because now when i go into Computer i can't even see an icon for the volumes any more- they show up in GParted as mounted but i don't have the option to unmount them.

i renamed the volumes from what they originally mounted as (disk, disk-1 under /media) to VMware_XP and VMware_Vista using **sudo chown user:group volume** and this is what i added to my /ect/fstab for the volumes to automount:

/dev/sdb1 /media/VMware_XP defaults 0 0
/dev/sdb2 /media/VMware_Vista defaults 0 0

any idea what i am doing wrong here?

---

### Post by jeffus_il on 2008-01-29
You fstabbed volumes will not show as icons any more, this is correct behaviour. You must now access them through the file system /media/VMware_XP and /media/VMware_Vista since after mounting they are now part of the file system. Of course you do not have an option to unmount them. If you really need to unmount them then use the umount command in a terminal. Or take them out of the fstab as they were previously.

---

### Post by Matt26 on 2008-01-29
thanks i wasn't aware of that- can i make an icon for them under the Computer location, as i am used to going there to access most of my files.

---

### Post by jeffus_il on 2008-01-29
Excellent, or use bookmarks in Nautilus.

---

### Post by Matt26 on 2008-01-29
is using Bookmarks the only way to do this?  is there a way that i can have an icon for the volume show up under the Computer location the way it did before i added the entries to /etc/fstab?  thanks.

---

### Post by legend2440 on 2008-01-29
Perhaps this will help
In terminal type 
gconf-editor

Then go to apps  >>  nautilus  >> desktop and put check next to volumes_visible

This will put icons on desktop and perhaps also in Places
Hope that helps

---

### Post by jeffus_il on 2008-01-29
Drag the bookmark onto your desktop!

---

### Post by Matt26 on 2008-01-29
where i should i be looking for access to these new volumes under Filesystem?  i'm not sure where they would be located.  thanks.

---

### Post by jeffus_il on 2008-01-29
Where you mounted them using fstab under the media folder

---

### Post by Matt26 on 2008-01-29
i went there and there are no folders for the volumes i am looking for... under /media.

---

### Post by jeffus_il on 2008-01-29
Those are the NTFS volumes, do they have data?

---

### Post by Matt26 on 2008-01-29
actually they are ext3 volumes labelled as VMware_Vista and VMware_XP.

and they do not have any data on them yet.

---

### Post by jeffus_il on 2008-01-30
So put some there, Your problem is a "non problem"

---

### Post by Matt26 on 2008-01-30
thanks for the suggestion, but how am i supposed to add anything to the volumes if i can't access them?  my issue is that i don't see these folders under the /media directory- the volumes have been added to /etc/fstab to mount to this location- and therefore i cannot access these volumes.

---

### Post by jeffus_il on 2008-01-30
> **Matt26 said:**
> thanks for the suggestion, but how am i supposed to add anything to the volumes if i can't access them?  my issue is that i don't see these folders under the /media directory- the volumes have been added to /etc/fstab to mount to this location- and therefore i cannot access these volumes.

You have to add the folders to the /media directory to mount at that point, otherwize the mount will fail.
Please post /etc/fstab
the output of mount
and the output of ls -l /media

---

