---
title: "Have FAT32 - need write access?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by tjp.thomas on 2006-07-31
HI There
I have a FAT32 partition on my HD, and it mounts nicely in Ubuntu... however, I cannot seem to be able to change the permissions on the drive in order for me to be able to store content on it. Can you help me?

---

### Post by OpsVentus on 2006-07-31
Sure, let's begin with you fstab. This is the file where Linux looks to see what to mount where and how.

In a terminal go:
#cat /etc/fstab

And tell us what it says.

Cheers,
Bart.

---

### Post by tjp.thomas on 2006-07-31
That was amazingly quick. I am not at my "own" computer (work work work...)... but when I get home, I will check!.. thanks!

---

### Post by drivel on 2006-07-31
You should USE mount.and fat32 can read and write by default in ubuntu.
You can modify /etc/fstab to auto monut.

---

### Post by OpsVentus on 2006-07-31
It should look something like this:
/dev/hda1 /mnt/mydisk fat32 auto 0 0

Cheers,
Bart.

---

### Post by tjp.thomas on 2006-07-31
Thanks again... I will experiment later today... will give feedback ;)

---

### Post by tjp.thomas on 2006-08-01
I still cannot get this to work. My fstab file is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb5       /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I tried adding this:
/dev/hdb1	/media/hdb1	fat32	defaults	0	1

But nothing has happened. I can see an icon indicating that the drives is there; but unmounted. When I try to right click -> mount, I get the following error:

mount: only root can mount /dev/hdb1 on /media/hdb1

Strange?

---

### Post by Indras on 2006-08-01
The default setting is to mount fat32 belonging to root.  The option "gid=46" sets the group id of every file mounted to "plugdev."  The "umask=077" in your fstab tells it to mask 007 over the default permissions (777) so as a result every file has permissions 770 (777-007=770).

You cannot change these file permissions using chmod or chown/chgrp, since the fat32 tables don't support these file options.  Therefore, it loads up the fat tables and overlays the settings from your fstab onto it in order to add it to the filesystem.  If you want to change the permissions on files, you have to change the way it is mounting them.

So if you want to change the owner of files on your drive, set a "uid=##" option, and "gid=##" for group.  To change the permissions, modify the "umask="

The most common thing people want to do is to mount it with full read/write access by all users, in which case just change umask=007 to umask=000 (you could just delete the umask entry, but I prefer to keep it in there as a reminder to put it back later if you want).

For reference, here's the FAT32 entry in my fstab for my second hard drive: 
/dev/hdb1 /storage vfat defaults,utf8,umask=000,gid=46 0 1
This is mounted with full read/write access for everyone, which is required if you want to share it with samba.

Sorry if I rambled, but this should help others with similar problems :)

Edit: Oh, if you're curious, the nls=utf8 option is to allow for extended characters in filenames, like japanese characters and such.

---

### Post by tjp.thomas on 2006-08-01
So... to compare... I use:

/media/hdb1

as my mount point? And you use

/storage as yours?

Should I change something there?

---

### Post by Indras on 2006-08-01
It doesn't matter what mount point you use, as long as there's an empty folder there for mount to put it on.  So go into your /media folder and make sure there's an empty folder called "hdb1" in there, if not, just "sudo mkdir hdb1"

---

### Post by tjp.thomas on 2006-08-02
Hi guys. I ended up re-installing due to other problems. Now it works. I found out that the FAT32 was not set to be active....  I guess that was what caused the problems in the first place. THANKS for all your help!!

---

