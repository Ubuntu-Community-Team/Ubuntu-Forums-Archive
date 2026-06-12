---
title: "Macbook Pro Died - Trying to access the files"
date: 2008-09-09
forum: Apple Hardware Users
---

### Post by bigfatdummy on 2008-09-09
My Macbook Pro died on Monday. I have Ubuntu system and have hooked the hard drive from my macbook to the ubuntu computer. For the most part, I can reload the software and OS onto the new HD I am installing into my Macbook, so I am not overly concerned about the loss of most the stuff. I do however want to grab my media off the drive. Since I am not the owner of the drive on Ubuntu, I am unable to access the User files. 

I have been trying to change permissions on the drive but I must be doing something wrong.

I have been using sudo chown -R myusername /media/Disk/Users/myusername/Pictures

I get back

chown: changing ownership of `/media/Disk/Users/username/Pictures': Read-only file system

What am I missing?

---

### Post by lswest on 2008-09-09
> **bigfatdummy said:**
> My Macbook Pro died on Monday. I have Ubuntu system and have hooked the hard drive from my macbook to the ubuntu computer. For the most part, I can reload the software and OS onto the new HD I am installing into my Macbook, so I am not overly concerned about the loss of most the stuff. I do however want to grab my media off the drive. Since I am not the owner of the drive on Ubuntu, I am unable to access the User files. 

I have been trying to change permissions on the drive but I must be doing something wrong.

I have been using sudo chown -R myusername /media/Disk/Users/myusername/Pictures

I get back

chown: changing ownership of `/media/Disk/Users/username/Pictures': Read-only file system

What am I missing?

Well, if you have another mac you could put it into target mode.  Otherwise, try unmounting the filesystem, and mounting it manually, seems the system is only mounting it as read-only.  Otherwise read-only access should allow you to copy the files, so maybe do that instead?

If the options above are not for you, please post back some more info about how you're mounting it, what filetype it is, what the permissions of the mountpoint are, etc.

---

### Post by bigfatdummy on 2008-09-09
Copying the files does not work either. 

This is the hard drive from my macbook pro. I removed it, threw it into a usb enclosure and hooked it up into my linux system, via usb. The drive popped up automatically. 

At this time I do not have a working mac. I ordered a new hard drive for the macbook but it will not arrive until Friday (320 GB 7200 Hitachi drive to replace this 320 GB western digital drive). 

Should I just be patient and wait until Friday to connect it to my Mac? I have been in the process of copying my media files to the Ubuntu computer to use on Boxee.

---

### Post by lswest on 2008-09-09
> **bigfatdummy said:**
> Copying the files does not work either. 

This is the hard drive from my macbook pro. I removed it, threw it into a usb enclosure and hooked it up into my linux system, via usb. The drive popped up automatically. 

At this time I do not have a working mac. I ordered a new hard drive for the macbook but it will not arrive until Friday (320 GB 7200 Hitachi drive to replace this 320 GB western digital drive). 

Should I just be patient and wait until Friday to connect it to my Mac? I have been in the process of copying my media files to the Ubuntu computer to use on Boxee.

Could you post the output of ```
sudo fdisk -l
``` corresponding to the drive you're trying to mount?  I really don't see what the problem could be.

---

### Post by bigfatdummy on 2008-09-09
Mount Point: /media/Disk
File System: hfsplus
Mount Options: ro nosuid nodev relatime umask=22 uid=0 gid=0 nls=utf8

---

### Post by bigfatdummy on 2008-09-09
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7086    56918263+   7  HPFS/NTFS
/dev/sda2            7087       59338   419714190    5  Extended
/dev/sda3           59339       60801    11751547+   7  HPFS/NTFS
/dev/sda5            7087       58061   409456656   83  Linux
/dev/sda6           58062       59338    10257471   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       19457   156288321    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       38914   312571223+  ee  EFI GPT

---

### Post by lswest on 2008-09-09
> **ro** nosuid nodev relatime umask=22 uid=0 gid=0 nls=utf8

change the ro to rw and see if that solves your problem.  If not, I'm out of ideas (no mac-formatted disk to play around with, sorry).  Worse comes to worse you might just need to wait til you have a working mac again.  Hopefully someone with a working macbook/Ubuntu dual boot can post more helpful suggestions.

Oh, also, check the permissions of the mountpoint (should be readable for any user, and write permissions to you and root)

---

### Post by kosumi68 on 2008-09-09
Writing to an hfsplus partition seems quite tricky - perhaps this link can help:

[http://ubuntuforums.org/showthread.php?t=14922](http://ubuntuforums.org/showthread.php?t=14922)

---

### Post by bigfatdummy on 2008-09-09
With gksudo nautilus I can see the folder contents but I am unable to copy them. 

Changing ro to rw also didn't work.

---

### Post by cyberdork33 on 2008-09-09
HFS+ will only mount readonly unless journaling is disabled. Unforunately, this can only be done in OSX. 

You can become root and copy the files from the drive to another location then you can chown them. If what you are attempting with nautilus is not working then there is likely another issue. (Try opening two root-owned nautilus windows and dragging between them).

I think the easiest solution is to fix the Mac with the new hard drive, then connect the USB drive to the Mac and use OS X to copy the files (since it will gladly work with HFS+).

---

### Post by bigfatdummy on 2008-09-10
I will just wait until I reload my Mac and then repost if I still am unable to resolve this situation.

Thanks for all the help so far.

---

### Post by pirateninjazombie on 2008-10-02
> **cyberdork33 said:**
> HFS+ will only mount readonly unless journaling is disabled. Unforunately, this can only be done in OSX. 

You can become root and copy the files from the drive to another location then you can chown them. If what you are attempting with nautilus is not working then there is likely another issue. (Try opening two root-owned nautilus windows and dragging between them).

I think the easiest solution is to fix the Mac with the new hard drive, then connect the USB drive to the Mac and use OS X to copy the files (since it will gladly work with HFS+).

I have got this to work as a workaround.

Open two terminals and put "sudo nautilus" in each, resulting in two open browser windows each with root privileges. Simply copy from the mounted External HDD to your new folder on desktop or wherever.

The problem with this method is that the resulting folder is still restricted to root edits, so you have to change the folder privileges. To do this, in your root nautilus window right click the folder to change, go to properties and select the permissions tab, here you can change to rw for Owner to your username and Groups to your usergroup if necessary. Click Apply Permissions to enclosed Files.

Happy Times.

---

