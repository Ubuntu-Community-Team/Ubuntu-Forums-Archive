---
title: "More FAT32 weirdness"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by feap on 2007-01-15
I just copied several assorted files to an external HDD formatted with FAT32. After I went to double-check that they actually were working (see thread below for reason for paranoia) they were all gone. No files, no directories nothing. The files don't show up anywhere on the HDD, not even in .trash or as hidden files.

But the weirdest thing is that the space was taken up. So now I can't even delete them. Is there something I can do to get the files back or at least reclaim the space? I'd rather not format.

[http://ubuntuforums.org/showthread.php?p=2008410#post2008410](http://ubuntuforums.org/showthread.php?p=2008410#post2008410)

---

### Post by taurus on 2007-01-15
As the azz man said in your original thread, did you just unplugged the external drive from your computer before unmount it?

---

### Post by feap on 2007-01-15
No, it's still on, mounted and working otherwise fine.

---

### Post by taurus on 2007-01-15
Then perhaps there is something wrong with that external harddrive!

---

### Post by feap on 2007-01-15
I have it in two partitions, both are FAT32. The other (larger) works as a swap disk and I use it daily without any problems. The other partition (smaller) exhibits the problem I described above and in the linked thread. So to me it sounds like an OS or file system issue.

---

### Post by taurus on 2007-01-15
Output of these two commands, please.

```
sudo fdisk -l
df -h
```

p.s.  What's the size of the file that you tried to save to your external harddrive?

---

### Post by feap on 2007-01-15
Here (sda2 is the partition having the problem. I recalled the larger partition was FAT32 as well, but it's not as shown):

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2569       19457   135660892+  83  Linux
/dev/sda2               1        2568    20627428+   c  W95 FAT32 (LBA)


--

Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              27G   22G  3.3G  88% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hdc              4.3G  4.3G     0 100% /media/cdrom0
/dev/sda1             130G  127G  2.8G  98% /media/usbdisk
/dev/sda2             150G  149G  887M 100% /media/COMPACTDRV

--

Size of files vary from a few megs to a few hundred. Nothing above 4 gigs if that's why you're asking.

---

### Post by taurus on 2007-01-15
So you created two partitions on your external harddrive, one with ext3 filesystem (/dev/sda1) while the second partition, /dev/sda2, is fat32 filesystem!  And looks like the second partition, /dev/sda2, is full so you can't write stuff to it anymore!  In fact, both partitions on your external harddrive are almost to the max capacity.  

What's the output of this command from a terminal?

```
ls -la /media/COMPACTDRV
```

---

### Post by feap on 2007-01-15
Your first paragraph is correct. Well, they both have a few hundred or a few gigs free.

Below is the command output. I copied the recent stuff to /Backup where it's not anymore. The earlier stuff mentioned in the other thread was in root and has been deleted, and the free space was reclaimed in that case. The SPACEXXX directories are photo RAW file backups which work fine.

total 516
drwx------ 9 h    h     32768 2007-01-15 14:57 .
drwxr-xr-x 7 root root   4096 2007-01-14 18:24 ..
drwx------ 5 h    h    131072 2007-01-15 15:05 Backup
drwx------ 3 h    h     65536 2006-12-16 04:56 SPACE008
drwx------ 3 h    h     65536 2006-12-16 05:07 SPACE009
drwx------ 3 h    h     65536 2006-12-17 13:47 SPACE010
drwx------ 3 h    h     65536 2006-12-17 14:19 SPACE011
drwx------ 4 h    h     65536 2006-06-22 00:49 SPACE012
drwx------ 2 h    h     32768 2007-01-15 14:57 .Trash-h

edit: I just unmounted (by r-clicking and ejecting from desktop) and reconnected the drive, didn't fix anything: still no reclaimed space and files missing.

---

### Post by taurus on 2007-01-15
```
ls -la /media/COMPACTDRV/Backup
```

---

### Post by feap on 2007-01-15
command output:

total 0

By r-clicking on the drive and checking properties, it shows "1734 items totalling 7.8GB" (out of 20GB total), but only 886MB free. So I'm missing ~11GB.

---

### Post by taurus on 2007-01-15
Do you want to remove everything in /media/COMPACTDRV/Backup?

```
sudo rm -rf /media/COMPACTDRV/Backup/*
```

Or

```
sudo du /media/COMPACTDRV
```

---

### Post by feap on 2007-01-15
First command didn't do anything, neither did the second (I did type in the correct admin pw). Directory structure and files are intact.

Here's the output of du:

32      /media/COMPACTDRV/.Trash-h
1571072 /media/COMPACTDRV/SPACE008/DCIM/100CANON
1571136 /media/COMPACTDRV/SPACE008/DCIM
1571200 /media/COMPACTDRV/SPACE008
1981696 /media/COMPACTDRV/SPACE009/DCIM/100CANON
1981760 /media/COMPACTDRV/SPACE009/DCIM
1981824 /media/COMPACTDRV/SPACE009
1991328 /media/COMPACTDRV/SPACE010/DCIM/100CANON
1991392 /media/COMPACTDRV/SPACE010/DCIM
1991456 /media/COMPACTDRV/SPACE010
1980416 /media/COMPACTDRV/SPACE011/DCIM/100CANON
1980480 /media/COMPACTDRV/SPACE011/DCIM
1980544 /media/COMPACTDRV/SPACE011
128     /media/COMPACTDRV/Backup
629952  /media/COMPACTDRV/SPACE012/DCIM/100CANON
630016  /media/COMPACTDRV/SPACE012/DCIM
896     /media/COMPACTDRV/SPACE012/.Trash-h
630976  /media/COMPACTDRV/SPACE012
8156192 /media/COMPACTDRV

---

### Post by feap on 2007-01-16
Anyone have any ideas? At this moment I'd be happy just to delete everything to reclaim the space, but that doesn't seem to help. Is there any other way apart from formatting?

---

