---
title: "harddisk seen as a removable drive? ; unable to mount"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by TheOther on 2007-02-15
Hello,

I have had some trouble installing ubuntu. But finally (I think due to wrong BOIS settings) my system is up and running. But... my old partitions still having XP, ME and Data are not visible. In the application 'Computer' the drives show as a CD-drive icon. When I tried to open for instance the ME partition (FAT32) the ' Computer' application complained: 'Unable to mount the selected volume'. The 'details' showed two errors:
-device /dev/hde1 is not removeble
-could not execute pmount

Because I had trouble installing I tried several thing. One thing I remember did put the drives on the desktop screen. This happend when I altered the origional '/media/hdf1' setting (mount point option of the partitioner of the install disk) to the root ('/'). 
The last (re)installation of ubuntu installed automaticaly whitout having any trouble. 
ME and XP are still bootable and the data partition is still there. 

Some information: I'm having two disks (IDE-ATA). First has three partition:ME, XP, Data. On the second disk I did the ubuntu installation (standard text installation of the alternate 6.06 CD-disk) that made two partitions:Ext3 and swap.

Where do I start to correct this? What did I do by altering the Mount point setting in the partitioner to '/'?

---

### Post by mssever on 2007-02-15
Can you post the contents of /etc/fstab for us?

---

### Post by TheOther on 2007-02-16
> **mssever said:**
> Can you post the contents of /etc/fstab for us?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdf1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdf5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

That's it. The system has (beside the two harddsiks) a CD-rom RW, a DVD player and a floppydrive. For what I understand (I'm new to ubuntu/linux) I don't see the hde1, hde5, hde6.

---

### Post by mssever on 2007-02-16
You need to add the proper entries into /etc/fstab for your windows partitions. See this thread for some excellent information: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you still have difficulties, post back...

---

### Post by VraiChevalier on 2007-02-16
I don't know if this will help or solve your situation but I was having a very similar experience (as I am a Gnoob!).

I formatted my drive with a partition for FAT32 so I could swap with WinXP. When I tried to access the FAT32 partition I received this error message:

Unable to mount the selected volume.
error: device /dev/hda4 is not removable
error: could not execute pmount

After some reading and research what I did to fix it was this;

From *Applications>Accessories[I]*[/I] open *Terminal[I]*[/I]. Then type in **gksudo gedit /etc/pmount.allow[B]**[/B] to open the file pmount.allow. Then enter on the last line the partition name (mine was /dev/hda4). Click save and close the editor. Then I went to the *Computer[I]*[/I]window and right clicked the FAT32 partition and chose *Mount Volume*. 

And it worked! Hope this may help.

---

### Post by TheOther on 2007-02-17
> **mssever said:**
> You need to add the proper entries into /etc/fstab for your windows partitions. See this thread for some excellent information: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you still have difficulties, post back...

Ok, I managed to mount ME and data partiions. I edit fstab with:
/dev/hde1 /mnt/winME vfat auto,ro,users 0 0
/dev/hde6 /mnt/data vfat auto,rw,users 0 0

Strange (to me) is that the ls -l shows the same rw-rights of the directory winME and data. 
drwxr-xr-x 13 root root 8192 1970-01-01 01:00 data
drwxr-xr-x 14 root root 4096 1970-01-01 01:00 winME
(this is not a blocking issue to me but can someone can tell me this is normal or not? I expected that the ro option resulted in less rw-rights the the rw option.)

More strange (and not working at all) is that the result of:
/dev/hde5 /mnt/winXP ntfs auto,ro,users 0 0
In the application computer there is a red cross on the directory /mnt/winXP and an error message pops up complaining I do not have permission. (But in terminal mode using sudo I also can't access the directory/partition)

I changed ntfs to ntfs-3g then the partition is not mounted and the error in computer is: unknown filesystem type 'ntfs-3g' 

What is the correct line if I only want read rights in the XP ntfs partition?

---

