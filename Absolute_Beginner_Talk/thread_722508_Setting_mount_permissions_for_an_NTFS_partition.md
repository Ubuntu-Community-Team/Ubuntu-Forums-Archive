---
title: "Setting mount permissions for an NTFS partition"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by siddjazz on 2008-03-12
Im a complete novice with linux. Have recently installed gutsy gibbon. Now i have 2 hard drives, ones a SATA and ones an IDE drive. 
I just cannot figure out how i can set mount permissions for the IDE drive for accounts other than mine(admin). I have tried 'chmod', 'chown' and then 'chmod' but no luck. 
Another strange observation is my IDE drive hda1, is not listed in the fstab file. This is what it looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=89518dad-8707-4f0e-b11d-2e156b85bf5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=72EC7B2DEC7AEB2D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=7C8F-961E  /media/sda5     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=E096-77E4  /media/sda6     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=313511dd-7d51-409b-95dd-7dbfc33e435b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


sda1, 5, 6 are partitions on the SATA drive(windows partition).
Is there any way i could manually add an entry for hda1?? If so how do i allow this disk to  be visible only to the admin and no one else??
oh yes, in case this is relevant in any way. When i log onto the admin account and access the hda1 disk, it prompts me to enter the admin password. But for subsequent accesses it opens it without a prompt.
Any help would be appreciated.

---

### Post by RedLXXXIV on 2008-03-13
If you get Automatix 2, you can install NTFS managing software with a couple clicks.

[Automatix install page]("http://www.getautomatix.com/wiki/index.php?title=Installation")

Be forewarned though, Linux (all flavours) is still unstable with NTFS partitions, and if you aren't careful, you can destroy your data on your NTFS partitions!

:) RedLXXXIV

---

### Post by siddjazz on 2008-03-14
thanks red will give it a shot.

---

### Post by jan quark on 2008-03-14
[B]automatix can cause severe compatibility issue, so use it at your own risk

but the usage is not recommened[/B]
you can install everything through the terminal or the synaptic package manager

---

