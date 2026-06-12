---
title: "How to include shared XP folder through proftpd in Ubuntu"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by alls0p69 on 2007-10-16
First post... here goes nothin.
I am about a month into Ubuntu now and want to add a folder shared from my xp machine to FTP server running proftpd on Ubuntu Feisty Fawn.

I have setup working fine based on this guide: [http://ubuntuforums.org/archive/index.php/t-79588.html](http://ubuntuforums.org/archive/index.php/t-79588.html)

With a few tweaks such as: I have separate folders mounted to the upload and download folders on a secondary hd (/media/disk/FTP & /media/disk/files respectively) No problems there.

I have a samba mounted XP network drive called Music on the Ubuntu desktop working just fine. I would like to add that drive/folder, read only, as a subdirectory in the FTPs download.  So basically; Is there a way to add network shares to my ftp server?

I have tried making a new directory called /media/disk/files/Muzak and mounting the samba share, but all I see is the folder and no files or folders within.

here is what it looks like

poop@ubuntu:/media/disk/files$ ls -l
total 364304
-rwxrwxrwx 1 poop poop   3425666 2007-09-11 20:46 DSC00149.JPG
-rw-r--r-- 1 poop poop 367342892 2007-10-02 11:19 House.avi
-rw-r--r-- 1 poop poop     10331 2005-08-22 12:03 logo.jpg
drwxr-xr-x 1 poop poop      4096 2007-10-16 15:18 muzak
-rw-r--r-- 1 poop poop   1883970 2007-10-16 13:54 Today.mp3

and the folders inside the network (muzak) drive look like

drwxr-xr-x 1 poop poop    4096 2006-04-25 20:52 Xzibit
drwxr-xr-x 1 poop poop    4096 2006-04-25 20:52 Yasmeen Sulieman
drwxr-xr-x 1 poop poop    4096 2006-04-25 20:52 Yellowcard
drwxr-xr-x 1 poop poop    4096 2006-04-25 20:52 Young Buck
drwxr-xr-x 1 poop poop    4096 2006-04-25 20:52 Young Rascals
drwxr-xr-x 1 poop poop    4096 2006-04-25 20:52 Zakk Wylde
drwxr-xr-x 1 poop poop    4096 2006-04-25 20:52 Zombies

I am not sure if this is a permissions thing or what.

Any help would be greatly appreciated.
Thanks in advance..

---

### Post by 1337455 10534 on 2007-10-17
DO you need read/write permissions for NTFS filesystem? Find "NTFS Configuration Tool" in the Add/Remove Programs" App.
My little 3 centcc.

---

