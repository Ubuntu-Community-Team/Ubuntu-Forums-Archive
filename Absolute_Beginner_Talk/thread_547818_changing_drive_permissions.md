---
title: "changing drive permissions"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by HappyFeet on 2007-09-10
i have a usb drive that i need to change permissions on so i can write to it. i heard i will need to know the path to the drive also. how do i find the path?

---

### Post by bodhi.zazen on 2007-09-10
The issue is also dependent of the file system on the USB drive as you set FAT/NTFS permissions different from linux permissions.

To show where you are mounted you can use :

mount

sudo ls -l /media

---

### Post by HappyFeet on 2007-09-10
thanks for the reply. i plugged in the drive and now read and write to it. i didnt do anything though. that's weird.

---

### Post by VoyeurOne on 2007-09-13
Not so weird at all, the permissions keep changing on my USB drive <500 Gig external USB 5 partitions FAT32>  sometimes they change when I reboot, sometimes they change on the fly, sometimes I can write to one partition and not the other, and sometimes I can send files to trash but the permissions change before I can delete from trash......

Please does anyone have any idea on how to permanently fix this problem???

---

### Post by VoyeurOne on 2007-09-13
This might help with my problem

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

---

### Post by VoyeurOne on 2007-09-13
drwx------ 21 pierre root    32768 1969-12-31 20:00 ADULT
lrwxrwxrwx  1 root   root        6 2007-08-05 12:21 cdrom -> cdrom0
drwxr-xr-x  2 root   root     4096 2007-08-05 12:21 cdrom0
drwxrwx---  1 root   plugdev 24576 2007-09-13 12:48 deskadult
drwxrwx---  1 root   plugdev 20480 2007-09-13 03:52 deskmovies
drwxrwx---  1 root   plugdev  4096 2007-09-13 00:07 deskmusic
drwxrwx---  1 root   plugdev 53248 2007-09-13 00:07 deskpictures
dr-xr-xr-x  1 root   root     4096 2007-09-09 05:22 FreeAgent Drive
drwx------ 15 pierre root    16384 1969-12-31 20:00 IAUDIO
drwx------ 34 pierre root    32768 1969-12-31 20:00 MOVIES
drwx------  9 pierre root    32768 1969-12-31 20:00 MUSIC
drwx------ 98 pierre root    32768 1969-12-31 20:00 PICTURES
drwx------  3 pierre root    32768 1969-12-31 20:00 TRANSFERS
drwxrwx---  1 root   plugdev 28672 2007-09-13 00:07 windows


The only drives I have a problem with are the ones that the drive name is in capital letters, the other drives are NTSF and I have no problems at all with them

That should be enough information to get some Linux Guru thinking

---

