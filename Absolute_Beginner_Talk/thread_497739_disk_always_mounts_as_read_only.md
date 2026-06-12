---
title: "disk always mounts as read only"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by onero on 2007-07-10
I have a 1st gen iPod Nano, and I fudged it somewhat, and now it only mounts in Ubuntu as read-only :( other external USB disks mount normally as read-write, but the ipod mounts as read-only. Is there any way I can fix this? Is there some file I have to edit or some lock I can delete?

As an extra note, I can use the ipod normally in Windows, and create/delete files normally, but there are a few corrupted directories / files that I can't delete even when I'm on Windows. Any thoughts?

---

### Post by Inxsible on 2007-07-10
> **onero said:**
> I have a 1st gen iPod Nano, and I fudged it somewhat, and now it only mounts in Ubuntu as read-only :( other external USB disks mount normally as read-write, but the ipod mounts as read-only. Is there any way I can fix this? Is there some file I have to edit or some lock I can delete?
 
As an extra note, I can use the ipod normally in Windows, and create/delete files normally, but there are a few corrupted directories / files that I can't delete even when I'm on Windows. Any thoughts?
 
Check the permissions/ownership on the mount point of the iPod. If they are not yours, take ownership of the mount point. Maybe that will help you write to it while in Ubuntu.
 
As for the folders you can delete, did you put something on the iPod while in Ubuntu earlier? Windows will probably not be able to delete those folders, so you might have to use Ubuntu to delete them which takes us back to your first problem.

---

### Post by onero on 2007-07-10
Yup, I own the folder and have permission to create and delete files. What happened is, I deleted some files in the ipod which stored them in the .trash folder of my user in the ipod. when I reattached the ipod, it was read only. In windows I restored the deleted files, but didn't delete some files in the trash folder; the next time I attached the ipod to windows, I couldn't delete the remaining contents of the trash folder because it was corrupt. And throughout this process, the ipod has only mounted in ubuntu as read-only.

I tried adding an entry in fstab and mounted the ipod manually, but it still mounts as read only. My fstab entry is:

/dev/sdb2 /media/IPOD vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

Any ideas? Losing the ipod data is fine, as I have backups, as long as I'm able to use it in ubuntu and windows.

---

### Post by Inxsible on 2007-07-10
> **onero said:**
> Yup, I own the folder and have permission to create and delete files. What happened is, I deleted some files in the ipod which stored them in the .trash folder of my user in the ipod. when I reattached the ipod, it was read only. In windows I restored the deleted files, but didn't delete some files in the trash folder; the next time I attached the ipod to windows, I couldn't delete the remaining contents of the trash folder because it was corrupt. And throughout this process, the ipod has only mounted in ubuntu as read-only.
 
I tried adding an entry in fstab and mounted the ipod manually, but it still mounts as read only. My fstab entry is:
 
/dev/sdb2 /media/IPOD vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
 
Any ideas? Losing the ipod data is fine, as I have backups, as long as I'm able to use it in ubuntu and windows.
 
Could you connect your iPod and then do a ```
sudo fdisk -l
```-l is lowercase L and post the result here?

---

### Post by onero on 2007-07-10
Hi, this is the output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Extended
/dev/sda5           38158       38913     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 2047 MB, 2047868416 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          10       80293+   0  Empty
/dev/sdb2              11         248     1911732    b  W95 FAT32
```


My ipod is sdb2 I think.

---

### Post by onero on 2007-07-11
Yay, I resolved my issue. The problem was caused by those corrupted directories I couldn't delete. I deleted them using Rockbox, and now i can write to the ipod again using Ubuntu :D Don't really know why they should cause that, but at least it's ok now ^^

---

### Post by ben2talk on 2008-03-30
I plugged in my SD card from my camera - and it loads as read-only.

I don't understand from this thread how to make it read/write. It's mine, and I want to be able to MOVE pictures and not just copy them!

What's going wrong? Why am I not allowed to change the permissions by clicking and checking the permissions boxes?

This is one more reason, I think, that linux sucks.... why can't I get the option to enter my password and gain elevated priviledge at the GUI to do the job?

---

