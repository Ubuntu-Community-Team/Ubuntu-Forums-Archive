---
title: "External USB drive permissions"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-12-25
Hi guys!

Im trying to plug in an external usb drive in my Ubuntu 5.10 with write permissions. I can only read but not write and when I try to change the permissions settings it tells me I cant do that.

Please help!


Thanks

---

### Post by Mustard on 2005-12-25
What is the file format of the external drive?

---

### Post by zaxer on 2005-12-25
[QUOTE=Mustard]What is the file format of the external drive?[/QUOTE]
Where can I see that info?

---

### Post by Mustard on 2005-12-25
Try this command in a terminal and look for a device like /dev/sda and see what it says for the file format at the end of that line under the System heading.  
```
sudo fdisk -l
```

Type this command if you want to read the manual for fdisk.

```
man fdisk
#hit the 'q' key to exit the manual
```

---

### Post by zaxer on 2005-12-25
[QUOTE=Mustard]Try this command in a terminal and look for a device like /dev/sda and see what it says for the file format at the end of that line under the System heading.  
```
sudo fdisk -l
```

Type this command if you want to read the manual for fdisk.

```
man fdisk
#hit the 'q' key to exit the manual
```[/QUOTE]

Ok, its NTFS. What then?

Thanks!

---

### Post by Mustard on 2005-12-25
Linux in a general sense cannot write to NTFS.  It can only read it.  The necessary information for linux to do so has not been released by Microsoft.  Linux developers are attempting to reverse engineer to find out how to write to NTFS, but at this stage it is experimental only.

The usual solution to this problem is to use fat32 to communicate between windows and linux, as both windows and linux recognise fat32.

If you wanted to you could try backing up your data from your usb drive onto a windows machine and then formatting the usb drive as fat32 instead, then putting the data back on to the usb drive, so that you can mount it with read/write permission in linux.

---

### Post by ubuntuuser on 2005-12-25
At present linux is not able to write onto NTFS partitions, at least not without kernel modifications. And even then it may still destroy your data, so you may want to reformat the drive to fat32 or a linux format like ext3.

---

### Post by Mustard on 2005-12-25
Just another thought.  I wasn't thinking to straight when I suggested the above solution.  You wouldn't need to backup to a windows machine as you can already read the contents of the usb disk.  You could simply put the contents of the usb drive on your linux machine (assuming you have space), then format the usb drive as fat32, then put the data back on to the drive, after mounting the usb drive with read/write permission.

---

