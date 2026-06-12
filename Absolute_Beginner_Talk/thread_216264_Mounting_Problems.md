---
title: "Mounting Problems"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by hatman on 2006-07-15
Been using ubuntu at work for the last month and half, no problems (only one hdd in there)... Come to putting it on my home pc and am unable to access any of the ntfs drives.

Got C: (hda1), D: (hdb1), E: (hdb5) and I: (hde1) and all show up in Computer - File Browser but when clicking on them it comes up with an error message

> UNABLE TO MOUNT THE SELECTED VOLUME
error: device /dev/hdb5 is not removable

error: could not execute pmount

added hde1 to fstab but then it comes up saying that
> 
mount: only root can mount /dev/hde1 on /media/windows

At the moment I need to keep hold of the ntfs drives (and their data) but the idea is to move away from M$ altogether...eventually...

Totally lost...tried some of the other things mentioned in the forum but to no avail...:( ](*,)

---

### Post by givré on 2006-07-15
To mount windows partition
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

But with this method you will not be able to write on your NTFS partition (still experimental, not really safe), so you have the choice
- Convert all your NTFS partition in FAT32, a filesystem that can be R/W by both linux & windows
- Convert all your partition in Ext3,  so you can keep all the functionnality of ext3, with no limitation of size (FAT32 is limited to a size file of 4G)
You will be able to R/W them from Windows with ext2fsd [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
- Keep them in NTFS and R/W them with fuse+ntfsprogs [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
it's more safe than with the kernel's driver, but it's still not really safe if you want to use them intensivly.

---

### Post by autocrosser on 2006-07-15
Take a look at my other mount post in this forum-- As givré said, writing to NTFS is expermental, but I find it needful every so often--in any case--it is a easy way to get access to you NTFS stuff..........

---

### Post by hatman on 2006-07-16
> **givré said:**
> To mount windows partition
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

But with this method you will not be able to write on your NTFS partition (still experimental, not really safe), so you have the choice
- Convert all your NTFS partition in FAT32, a filesystem that can be R/W by both linux & windows
- Convert all your partition in Ext3,  so you can keep all the functionnality of ext3, with no limitation of size (FAT32 is limited to a size file of 4G)
You will be able to R/W them from Windows with ext2fsd [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
- Keep them in NTFS and R/W them with fuse+ntfsprogs [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
it's more safe than with the kernel's driver, but it's still not really safe if you want to use them intensivly.
Can they be converted 'on the fly' as it were, like you can from FAT32 to NTFS?

I've managed to get them mounted and read the data on them, but I have to mount them manually (it's not a problem)... Converting them to ext3 is a better idea and helps with the ultimate goal of moving away completely from m$

@autocrosser... thanks for the advice, I have no need atm to be able to write to ntfs :D

EDIT: After googling it looks like it's a no-brainer... As luck would have it I have an external USB hdd, so it looks as if I'll have to move the data to that and format the drive as ext3...

---

