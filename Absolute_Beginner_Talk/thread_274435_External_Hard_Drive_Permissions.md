---
title: "External Hard Drive Permissions"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by divineleft on 2006-10-09
Hello, I'm using a usb external hard drive, but for some reason it won't let me change the owner or permissions, even in super-user mode. I have read and execute permissions, it just won't let me have write access. Here's my fstab:

```

/dev/hda1        /boot           ext2    defaults     1 2
/dev/hda2        none            swap    sw           0 0
/dev/hda3        /               ext3    defaults     0 1
/dev/sda1        /media/MYBOOK   vfat    defaults     0 0
none              /proc           proc    defaults     0 0
none              /dev/shm        tmpfs   defaults     0 0

```

I've tried almost every option out there, user, nouser, ect. Any suggestions?

---

### Post by divineleft on 2006-10-09
bump...

---

### Post by salguod on 2006-10-09
I have the same problem with the macintosh partition of my dual-boot powerbook G4. I also feel I have tried everything, but nothing seems to allow me to write to it (I can read it though).
My PCMCIA card and USB stick/CF card reader work fine.

this is my /etc/fstab:
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5       /media/mac      hfsplus     rw,umask=0		0       0
/dev/sda1       /media/usb1     auto    rw,user,auto    0       0
/dev/sdb1       /media/usb2     auto    rw,user,auto    0       0
/dev/hde1       /media/pcmcia   auto    rw,user,auto    0       0

any help is appreciated!
salguod

---

### Post by divineleft on 2006-10-09
Anybody? Please?

---

### Post by divineleft on 2006-10-10
:( :( :( :(

---

### Post by divineleft on 2006-10-10
bump

---

### Post by dannyboy79 on 2006-10-10
i found this on gogle for ya'll because i am not at home to post you my fstab entry. gogle is your friend don't forget.

In terms of the way rwx permissions work with FAT32 mounts:

The default permissions for a mounted FAT32 volume are rwx for root, but only rx for normal users.

In Linux, permission control works differently for FAT32 and NTFS filesystems than it does for native Linux filesystems (ext2, ext3, reiser, etc.):

1. The UNIX permissions of a directory onto which you mount a Windows filesystem can't be changed while the fileystem is mounted. Unmount the Windows partition; you should then be able to chmod the permissions of /mnt/Windows. You will need to set the appropriate Linux rwx permissions on the /mnt/fat folder and set the permissions for the FAT partition (as described below) in order to grant everyone write access.

2. Windows doesn't support UNIX-style permissions, and you can only apply permissions to the entire filesystem, not to individual Windows files/folders. This is done with the "umask" option of the mount command. In /etc/fstab, change the mount entry for your Windows partition to this:

/dev/hda6 /mnt/fat vfat users,defaults,umask=000 0 0

or if you no you arew going to have long filenames you could use this instead

/dev/hda6 /mnt/fat/ vfat iocharset=utf8,umask=000 0 0

obviously you need to change the hard drive designationa and partition number for your own (example: hda6) and also the mount directory. I would create it in media not mnt but that's just what I copied from gogle.


(the "users" option allows anyone to mount/unmount the drive and overrides the default , which is that only root is allowed to mount/unmount.)

- When issuing the mount command manually, the syntax is:

mount -t vfat -o umask=000 /dev/hda6 /mnt/fat


The value of the permission bits used with umask are the opposite of those used with the chmod command. For example, the following pairs are equivalent:

umask=000 and chmod 777
umask=022 and chmod 755

--------------------------------------------------------------------------------

---

### Post by divineleft on 2006-10-10
Yay, it works. Except now I can't execute anything from it, even though the permissions are 777. I can't even execute anything in root. I'll get something like this:
> 
bash: ./slope: Permission denied


---

### Post by divineleft on 2006-10-10
Ok, I fixed it. If anybody wants rwx access to a fat32 drive, use these options:

```
/dev/hda1	 /boot	 	 ext2	  defaults	 1 2
/dev/hda2	 none            swap     sw      	 0 0
/dev/hda3	 /	 	 ext3	  defaults	 0 1
/dev/sda1        /media/MYBOOK   vfat     umask=000,uid=justin,gid=users 0 0 
none        	 /proc     	 proc     defaults       0 0
none        	 /dev/shm  	 tmpfs    defaults       0 0
```

replacing justin with your username

---

### Post by dannyboy79 on 2006-10-10
> **divineleft said:**
> Ok, I fixed it. If anybody wants rwx access to a fat32 drive, use these options:

```
/dev/hda1	 /boot	 	 ext2	  defaults	 1 2
/dev/hda2	 none            swap     sw      	 0 0
/dev/hda3	 /	 	 ext3	  defaults	 0 1
/dev/sda1        /media/MYBOOK   vfat     umask=000,uid=justin,gid=users 0 0 
none        	 /proc     	 proc     defaults       0 0
none        	 /dev/shm  	 tmpfs    defaults       0 0
```

replacing justin with your username


i am sure you forgot to do this, "You will need to set the appropriate Linux rwx permissions on the /mnt/fat folder and set the permissions for the FAT partition (as described below) in order to grant everyone write access." otherwise I think it would have worked. Regardless, I am glad you got it. You're welcome.

---

### Post by salguod on 2006-10-10
Turns out mine was a bit more complicated.

I finally found out that for Macintosh partitions (hfsplus) to be read-write by ubuntu, the mac partition in Mac OS cannot be "journaled." I am now able to access the Mac partition! To see if your Mac hhard drive or partition is "journaled", boot into Mac OS and select the partition (in my case it was the entire hard drive) and use "get info" (apple+i). the word "journaled" apprears next to the format type of the disk.

I'm not really sure what that means, but i turned it off using the information from the following post:
[http://www.ubuntuforums.org/archive/index.php/t-190840.html](http://www.ubuntuforums.org/archive/index.php/t-190840.html)
------------------
In order to write to the hfs+ from the linux side, you have to disable journaling on the hfs+ volume from the os x side.

From terminal in os x, this command: diskutil disableJournal /
------------------

I find this odd because I used the exact same mac partition under ubuntu 5.10 with no problems. When I upgraded (from an install CD) to 6.10, the problem appeared.

---

