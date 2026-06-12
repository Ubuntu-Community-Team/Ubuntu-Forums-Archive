---
title: "Mounted fat32 partition write access"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Silik on 2006-11-25
Hi im new to ubuntu
I have a problem, my hardrive is partitioned (Windows XP-Datafat32-Ubuntu) but im having write access problems with some folders on the the data drive(see attachment) i cant write to my pics or music etc.
I followed some instructions found on this board to get it mounted but ran into this problem, i also tried adding uid=1000 or gid=1000 which i found on another post but that hasn't worked, heres my fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3525f6b9-c848-4305-bc80-0914a5bf046d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=007ef2c8-3e11-4989-99b2-4e77a98fad32 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2 /media/windows vfat iocharset=utf8,gid=1000,umask=000 0 0

Thanks.

---

### Post by taurus on 2006-11-25
Try to remove the "gid=1000" from the last line of your /etc/fstab and reboot.  Now, see if you can write to everything in /media/windows.

---

### Post by Silik on 2006-11-25
Thanks for the quick reply. I never had gid when i first mounted it and had the same problem, i did a search and someone suggested adding it, but that hasn't worked also.

---

### Post by jerrykenny on 2006-11-25
then try   umask=000   for the fat partition

---

### Post by Silik on 2006-11-25
Ok this is what i have now
/dev/sda2 /media/windows vfat iocharset=utf8,umask=000 0 0
but its still not letting me write to my pictures, videos and music.

---

### Post by taurus on 2006-11-25
You need to reboot...

---

### Post by Silik on 2006-11-25
No still nothing, the only thing i can think of is that they were created by xp when i set the "my documents" to point towards the d: drive the others were created by me after although the "my received files" folder is ok :confused:

---

### Post by nixclusive on 2006-11-25
mount the vfat filesystems with gid=46. that group is plugdev in the default installation and allows normal users write access.

---

### Post by nixclusive on 2006-11-25
and yeah, change the umask to 022 as well.

---

### Post by nixclusive on 2006-11-25
a mount /dev/sda2 -o remount,rw should work as well after you edit fstab

---

### Post by Silik on 2006-11-25
This is what i have
/dev/sda2 /media/windows vfat iocharset=utf8,gid=46,umask=022 0 0
The little lock icon has gone from the folder but i cant write to any off the folders now.

---

### Post by taurus on 2006-11-25
> **Silik said:**
> This is what i have
/dev/sda2 /media/windows vfat iocharset=utf8,gid=46,umask=022 0 0
The little lock icon has gone from the folder but i cant write to any off the folders now.
Because you use "umask=022" which means you can only read but not write to it!  Change it to "umask=000" if you want to write to it.

---

### Post by Silik on 2006-11-25
Still no luck, but i found a way around it, i created 3 new folders in ubuntu called "music" "pictures" and "videos" then booted into windows and dragged all my files out of the "my music" etc folders, then deleted them and i can now write to them.

I did a test also and added "My" back to the new folder names and it locked me out again, so i put it back.

---

### Post by jerrykenny on 2006-11-25
I dont think you need options other than umask=000 ,  but maybe its an ownership thing, try

sudo chown -fr taurus /media/windows

to recursively change ownership of the filesystem to yourself

---

