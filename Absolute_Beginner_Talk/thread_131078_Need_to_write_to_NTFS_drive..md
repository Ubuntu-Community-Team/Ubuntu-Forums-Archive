---
title: "Need to write to NTFS drive."
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Woggie on 2006-02-15
Is it possible to do that withour re-formatting?  If not, how do I re-format the drive?  On the "Disks" section the format buttom is greyed out.

---

### Post by patrick295767 on 2006-02-15
to write on ntfs is possible : paragon ntfs for linux
[http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)
  
The prob is that u may have some troubles (loose data) ...
  
Passing in FAT32 or EXT -linux type partitions is maybe the better solution.
  
Greetings

Pat

---

### Post by deBaas on 2006-02-15
[QUOTE=Woggie]Is it possible to do that withour re-formatting?  If not, how do I re-format the drive?  On the "Disks" section the format buttom is greyed out.[/QUOTE]
It is not possible without the risk of losing your data. A good program to remove/add and format partitions is gparted. To install type in a terminal:
```
apt-get install gparted
```
good luck.

---

### Post by poofyhairguy on 2006-02-15
[QUOTE=Woggie]On the "Disks" section the format buttom is greyed out.[/QUOTE]

You have to unmount the drive for you to be able to format it. A Live CD is GREAT for that task!

---

### Post by Woggie on 2006-02-15
Ok, so I can pull off the media I have on the drive, format it and put it back on right?
I want to make sure before I try to screw something up.:-k

---

### Post by TrendyDark on 2006-02-15
You *CAN* get into the drive and move things to and from another drive, but you're risking the lose of data in the process. NTFS + Linux = Bad idea

---

### Post by Woggie on 2006-02-15
Ok, I've removed the data I wany to keep from the NTFS drive and put it on my main drive.  I have umaunted the secondary drive and I am ready to format.  Is this a good idea or not?  I am confused.:confused:

---

### Post by jimrz on 2006-02-15
if your windows partion is that ntfs drive and you want to keep it, then you do not want to format the drive but rather shink the ntfs partition (be sure to defrag first, at least once) and then create a new partion and format it as FAT32 (read/writeable by both linux and win). gparted from the live cd will do this as well, or better yet if you have partition amgic do it with that from windows.

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=jimrz](be sure to defrag first, at least once)[/QUOTE]
in windows' safe mode preferably

---

### Post by eylisian on 2006-02-16
make sure you have ntfsprogs installed. Ubuntu by default I believe will mount ntfs read write in /etc/fstab. If not,

sudo mount -o remount,rw /dev/hd*

have good backups.

---

### Post by bartbes on 2006-02-16
I actuallu did the same, put all the data of the NTFS drive on my harddisk converted it to FAT32 and put it back, I needed that partition because my Virtual Machines (VMWare) are on it..

---

### Post by patrick295767 on 2006-02-16
[QUOTE=Woggie]Is it possible to do that withour re-formatting?  If not, how do I re-format the drive?  On the "Disks" section the format buttom is greyed out.[/QUOTE]
  
If you would like to do it via bootable cd, you could also have a quick look to this thread:
[http://www.ubuntuforums.org/showthread.php?t=131277](http://www.ubuntuforums.org/showthread.php?t=131277)
  
Greetings, 

Pat'

---

