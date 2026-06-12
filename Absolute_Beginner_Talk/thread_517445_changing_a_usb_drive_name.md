---
title: "changing a usb drive name"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-08-04
I have a usb drive that i want to change the name on.
I have read some other threads and tried to change another usb drive.
I changed the mount point  through settings but now it won't mount.
How do i do this the correct way.

---

### Post by orb9220 on 2007-08-04
Post your fstab.

Usually when it doesn't mount it is because people try to mount to a non-existence or misspelled folder.

Example: /dev/sda1 /home/Drives/xp Is there a folder in home called **Drives**? and did I create a folder named** xp** in **Drives**?

I had this problem where I had used **drives** instead of **Drives** in my fstab.
Also another time I did not have the target folder created.

---

### Post by Inxsible on 2007-08-04
since its an external drive, try mounting it with pmount

```
sudo pmount /dev/Xd*? MOUNT_POINT
```where X = s or h
* = a,b,c...
?=1,2,3...

and MOUNT_POINT is a name of your choosing. pmount automatically creates a folder under /media, so make sure you choose a name which is NOT already present under /media

---

### Post by johntkucz on 2007-08-15
> **thesonisshining said:**
> I have a usb drive that i want to change the name on.
I have read some other threads and tried to change another usb drive.
I changed the mount point  through settings but now it won't mount.
How do i do this the correct way.

Not knowing your specific parameters (OS, other possible conflicting installations, other variables, etc.), inhibits one from having full certainty of efficacy, but this general bit came to mind,

Linux is so cool because you can add any harddrive and make it “normal architecture” that automatically mounts by adding to the /etc/fstab file, creating a directory for it under /media/ folder. Note: remarkable how like this is with Big Brother updates. Everything must be updated and cross-referenced if a “BB surplus reference was changed for example”. To add a constant external drive you have to change /etc/fstab, /media/ references to it! Then it shows up in Places.
Also, realized that me criticizing with evidence why some advice is wrong is very similar to showing command line errors in terminal! It's not insulting; quite informative and helpful! A person who looks at it as insults shouldn't really be using it!

I think you need to change
/mnt
/media
/etc/fstab
 
to fully change a drive name...totally not sure on this (speak from reading experience, not so much "doing experience" with this reference), but that's the gist of it
> 1. The first thing to do is create a mount point, which is a directory that will act as a
location where you can tell mount to make the disk accessible.
&#9632;Note The mount point doesn’t necessarily have to be empty or new! You can use any directory as a mount
point, and as long as the file system is mounted, the original contents of the directory will be invisible.
However, to avoid confusion, it’s best to create a new independent mount point.
You can create the new directory anywhere, but under Ubuntu, the convention is
to create it in the /media directory. Therefore, the following command should do
the trick (note that you need to use the sudo command, because writing to any
directory other than your /home directory requires administrator privileges):
sudo mkdir /media/newdisk
2. You now need to know what kind of partition type is used on the disk, because you
need to specify this when mounting. To find this out, use the fdisk command. Type
the following exactly as it appears:
sudo fdisk -l /dev/hdb
3. This will list the partitions on the second disk drive (assuming an average PC
system). With most hard disks used under Windows, you should find a single partition
that will be either NTFS or FAT32. The examples here assume that this is hdb1.
&#9632;Caution Be aware that fdisk is a dangerous system command that can damage your system. The
program is designed to partition disks and can wipe out your data if you’re not careful!
4. With this information in hand, you’re now ready to mount the disk. For a FAT32
disk, type the following:
sudo mount -t vfat –o umask=000 /dev/hdb1 /media/newdisk
302 CHAPTER 14 &#9632; UNDERSTANDIN G LINUX F I L ES AND USERS
For an NTFS disk, type the following:
sudo mount -t ntfs -o umask=0222 /dev/hdb1 /media/newdisk
The -t command option is used to specify the file system type. The -o flag indicates
that you’re going to specify some more command options, and you do so in the
form of umask, which tells mount to ensure that the directory is readable (and
writable in the case of the FAT32 drive). After this, you specify the relevant file in
the /dev directory (this file is only virtual, of course, and merely represents the
hardware), and then specify the directory that is acting as your mount point.
&#9632;Note Although the fstab file refers to UUID numbers, for a temporary mount, it’s fine to refer specifically
to the hardware within the /dev directory.
Now when you browse to the /mnt/newdisk directory by typing cd /mnt/newdisk, you
should find the contents of the hard disk accessible. You should also have found that a
new icon appeared on the desktop for the file system which you can double-click to access
the new disk via Nautilus.
For more information about the mount command, read its man page (type man mount).

---

### Post by vanadium on 2007-09-04
To change the drive name of a removable USB, you should not be messing with fstab or be mounting manually. It suffices to change the disk label. How you do it depends on the file system on the disk.  See here for a round-up. [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive). Ubuntu will automatically use the label as the name for the mount point.

---

