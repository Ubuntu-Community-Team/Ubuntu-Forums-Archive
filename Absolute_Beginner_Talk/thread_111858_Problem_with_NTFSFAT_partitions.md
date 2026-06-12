---
title: "Problem with NTFS/FAT partitions"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by lemmy999 on 2006-01-03
Just rebuilt my machine with XP on a 10Gb NTFS partion, Ubuntu on a 10Gb EXT3 partion and a 50Gb FAT32 partion to share all my data. Have attempted to mount both partitions but am getting the following error message.

chris@ubuntuchris:~$ sudo mount -a
[mntent]: line 2 in /etc/fstab is bad
mount: /dev/hda1 already mounted or /windows busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1

The fstab output is 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda6       /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

I made a backup of the original fstab, can i revert to it? or can i modify the current one so that i can mount and access both NTFS and FAT partition?

---

### Post by bluefrog on 2006-01-03
sudo umount /dev/hda1 first

james

---

### Post by lemmy999 on 2006-01-03
OK tried that- output says

chris@ubuntuchris:~$ sudo umount /dev/hda1
Password:
chris@ubuntuchris:~$ sudo mount -a
[mntent]: line 2 in /etc/fstab is bad

??

---

### Post by Mustard on 2006-01-03
Is the /dev/hda2 supposed to be ext3 file system?  I'm just going off what you wrote in your original summary.  Where does the reiserfs file system come into it?

---

### Post by lemmy999 on 2006-01-03
initially i partitioned the drive as reiserfs. when i installed Ubuntu i think it reverted it to ext3. Can i just delete that line of the fstab?

---

### Post by Mustard on 2006-01-03
I wouldn't think you could delete that one.  Can you run this command in terminal and paste the output in here?

```
sudo fdisk -l
```

---

### Post by lemmy999 on 2006-01-03
Right- done that - output is  

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1303    10466316    7  HPFS/NTFS
/dev/hda2            1304        2598    10402087+  83  Linux
/dev/hda3            2599       10011    59544922+   f  W95 Ext'd (LBA)
/dev/hda5            2599        2989     3140676   82  Linux swap / Solaris
/dev/hda6            2990       10011    56404183+   b  W95 FAT32

---

### Post by Mustard on 2006-01-03
Hmmm..if you are on gnome can you go to your Systems>>Administration>>Disks menu choice and check out what file format is listed for the partition /dev/hda2?

---

### Post by lemmy999 on 2006-01-03
/dev/hda2 shows as a ReiserFS partition

---

### Post by Mustard on 2006-01-03
Ok..thats good then. :)

Now to the windows drives...I'm just going to look at your /etc/fstab again..

Have you thought about mounting them in your /media directory?

---

### Post by Pablo_Escobar on 2006-01-03
Try
sudo umount -a
sudo mount -a

If that doesn't maybe mounting to /media/windows and /media/fat_drive  would do some good.

EDIT : Sorry for jumping in :)

---

### Post by Mustard on 2006-01-03
Personally, I would use this script to automatically mount the drives and make the correct fstab entries...

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

If you want to use it, just make sure you remove the entries from your /etc/fstab first that refer to your windows partitions (or even just comment them out with the # symbol), then umount the windows partitions as well.  Then run the script following the instructions at the wiki page.  Its pretty easy to use and could save you a lot of mucking around.

---

### Post by lemmy999 on 2006-01-03
Sorry, but i may need some help here. Do i need to create a new directory?

---

### Post by Pablo_Escobar on 2006-01-03
sudo mkdir /media/windows
sudo mkdir /media/fat_drive

remember to change fstab entries

---

### Post by lemmy999 on 2006-01-03
Mustard

Tried your suggestion. Still appears to be a problem. output is 


chris@ubuntuchris:~$ sudo bash diskmounter
By default the disks will be writable only by root and
chris (chris)
Do you want to make the disk writable by all users instead? (y/n)
y
Ignoring /dev/hda1 - already in /etc/fstab
Ignoring /dev/hda6 - already in /etc/fstab
No usable windows/mac partitions found
chris@ubuntuchris:~$

---

### Post by Pablo_Escobar on 2006-01-03
Remove all windows partitions entries from fstab and run the script again.

---

### Post by meborc on 2006-01-03
this is how i mount my **FAT32** partition, hope that it helps

1) i make a directory in **/media/** called **fat32** ```
*sudo mkdir /media/fat32*
```
2) i find my **fat32** partition is **hda5...** i got it by doing ```
*sudo fdisk -l*
```
3) i mount my **fat32** partition ```
*sudo mount /dev/hda5 /media/fat32 -t vfat -o umask=000*
```

this is how i do it... i have to repeat ponit nr 3 every time i boot... but i'm too lazy to change that... hope this helps :rolleyes:

---

### Post by lemmy999 on 2006-01-03
P_E & Mustard

Success!! Thank you very much for your time!

---

### Post by Mustard on 2006-01-03
Well done. :)

---

