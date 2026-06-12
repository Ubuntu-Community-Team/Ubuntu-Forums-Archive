---
title: "External Hard Drive Issue !"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by new on 2008-03-17
ok ..i have had my external hard drive for a while and it was working prefectly...it is formated in FAT32 so it can be used in windows and ubuntu but it is mainly used for my ubuntu...it worked fine...but now recently ..i had deleted some files...and the space available wont change...it keeps saying 1 GB free space but when i plug it into my windows pc...it says 27 GB free space why is it not showing the space in my ubuntu or why when i try to add stuff it says it doesnt have enough space although it clearly does...cause the file count shows...20 + gb free but the pie chart only shows 1 GB... PLEASE HELP !! thanks u

---

### Post by ziroday on 2008-03-17
The reason you don't have enough space is that when you delete a file in Ubuntu it is saved to .Trash file on the drive. To see and delete the .Trash file press CTRL+H in Nautilus to view all hidden folders. Then you can just delete the .Trash file as normal

---

### Post by Rocket2DMn on 2008-03-17
The folder will appear at the root of the mount point, probably with your username attached, like /media/disk/.Trash-*yourusername*

---

### Post by Atomic Dog on 2008-03-17
An easier way is to open Nautilus (the file browser), open the external drive, click on "View" then "Show hidden Files."  At this point you will see the .trashes folder.  Open it and then highlite the files and press delete button.  They will be permanantly deleted.

---

### Post by jan quark on 2008-03-17
you can also use this terminal command but **use it very cautiously ** do not change it

```
sudo rm -Rf ~/.Trash/*
```

---

### Post by new on 2008-03-17
hey guys...i tried all the ways..and it is saying the folder cant be found...and when i apply show hidden files...nothing is coming up ! sigh !!

---

### Post by Rocket2DMn on 2008-03-17
Can you please post the output of
```
ls -la /media/*mountpoint_of_external_drive* | grep .Trash*
ls -la ~/.Trash
```

---

### Post by mrGRINCH on 2008-06-24
I'm having a similar problem. Here's what happened.

I had Ubuntu 8.04 Hardy Heron installed and I was removing some java components and I selected too many and I noticed it was uninstalling stuff it shouldn't be so I shut my laptop off and then tried to reboot but I only had the text interface not GUI.  So I got my live cd and booted up to see if all my files were still there, which they are. I have an external HDD and I got that and made space on it so I could copy all my files from my laptop over onto it. I ran out of space with 13GB of stuff left to copy over so I plugged my external HDD into my windows PC and copy some files over onto it a deleted a few other things and I made enough free space to copy the rest of my stuff over from my laptop but when I plug my External HDD back into my laptop it says I don't have enough space. When I right click and go to properties it says in the Contents: 17300 items, totaling 444.2GB but in the pie chart it says 465GB used and only 689.5MB free. The total drive capacity is: 465.6GB and the Filesystem type is vfat. 

I've made hidden files visible but I don't see any .trash folder. There is a "System Volume Information" folder and a "Recycled" folder, I deleted the files in System Volume Information, and I tried deleting the files inside the Recycled folder but it says I don't have permissions. The folder inside the Recycled folder has the name "Di51.Trash-ubuntu" and it has another folder inside it then another folder inside that and so on for a heap of folders. When I look at the properties of the folder though it only says it's 512KB. 

I don't see any other folders or files showing up. 

Here's a print out of these commands.

ls -la /media/mountpoint_of_external_drive | grep .Trash* 

ls: /media/mountpoint_of_external_drive: No such file or directory

and 

ls -la ~/.Trash

total 0
drwx------  2 ubuntu  60 2008-06-25 02:39 .
drwxr-xr-x 22 ubuntu 780 2008-06-25 02:39 ..

---

### Post by Rocket2DMn on 2008-06-25
"/media/mountpoint_of_external_drive" is only symbolic, you have to substitute that actual mount point for that, like /media/disk or something.  This thread is old, you should start a new thread in the beginners forum area - [http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)
Click the link near the upper left for New Thread.

---

### Post by mrGRINCH on 2008-06-25
I tried to start a new thread but it says I don't have permission to.

I tried doing the command again replacing it with My Book which is the name of my external HDD but it does My and Book separately because of the space. How would I type it in to make it work properly?

---

### Post by Rocket2DMn on 2008-06-25
surround My Book with quotations or use \ as an escape character
"My Book:
My\ Book

---

### Post by mrGRINCH on 2008-06-25
Okay I got this.

drxw------  3 ubuntu root   32768 2008-06-25 -2:55 .Trash-ubuntu



So does anyone have any ideas on how I can fix it?

---

### Post by Rocket2DMn on 2008-06-25
What exactly are you trying to do?  Delete that folder?  Post these commands for me while in that directory that you copied and pasted that from:
```
pwd
ls -la
ls -la .Trash-ubuntu/
```

---

### Post by mrGRINCH on 2008-06-25
Did you read my earlier post? My problem is I have deleted stuff from my external HDD using my windows computer but when I plug my external into my ubuntu laptop it's saying I don't have space on it. When I do right click properties it shows I have space in the "Contents" but the pie chart says I don't. I have just over 13GB of free space but when I try to copy stuff to it, it says I don't have the space.

What I did yesterday with the previous commands was open terminal and put the commands in, I didn't cd to my external drive first, is that wrong? Here's the out puts again for the previous ones after doing cd to my external drive.

ubuntu@ubuntu:/media/My Book$ ls -la /media/"My Book" | grep .Trash*
drwx------  3 ubuntu root   32768 2008-06-25 02:55 .Trash-ubuntu

ubuntu@ubuntu:/media/My Book$ ls -la ~/.Trash
total 0
drwx------  2 ubuntu ubuntu  60 2008-06-26 00:27 .
drwxr-xr-x 23 ubuntu ubuntu 760 2008-06-26 01:45 ..

Here's what I get for your new commands.

ubuntu@ubuntu:/media/My Book$ pwd
/media/My Book

ubuntu@ubuntu:/media/My Book$ ls -la
total 26944
drwx------ 14 ubuntu root   32768 1970-01-01 00:00 .
drwxr-xr-x  3 root   root     100 2008-06-26 01:43 ..
-rwx------  1 ubuntu root 2536182 2008-06-18 16:56 ********.JPG
-rwx------  1 ubuntu root 2536182 2008-06-23 05:28 ********.JPG
-rwx------  1 ubuntu root   15886 2008-06-17 11:05 ********.png
drwx------ 25 ubuntu root   32768 2008-06-23 02:53 All
-rwx------  1 ubuntu root   48689 2008-06-07 14:38 ********.JPG
-rwx------  1 ubuntu root    7747 2008-06-03 00:19 ********.odt
-rwx------  1 ubuntu root   54499 2008-06-23 05:22 ********.html
-rwx------  1 ubuntu root    8908 2008-05-17 03:01 ********.odt
-rwx------  1 ubuntu root    9136 2008-06-12 06:21 ********.odt
-rwx------  1 ubuntu root 9083705 2008-06-17 23:44 firefox-3.0.tar.bz2
-rwx------  1 ubuntu root    8072 2008-06-18 09:23 ********.odt
-rwx------  1 ubuntu root 3044538 2008-06-19 10:59 install_flash_player_9_linux.tar.gz
drwx------ 13 ubuntu root   32768 2008-06-24 08:07 Laptop
drwx------ 84 ubuntu root   32768 2008-06-12 22:24 Movies
-rwx------  1 ubuntu root  106496 2008-06-12 11:56 ********.doc
-rwx------  1 ubuntu root   97792 2008-06-17 08:14 ********.doc
-rwx------  1 ubuntu root     263 2008-05-13 02:44 Mozilla Firefox.desktop
drwx------  2 ubuntu root   32768 2008-06-10 22:57 Naruto
-rwx------  1 ubuntu root   97792 2008-06-18 15:09 ********.doc
-rwx------  1 ubuntu root    6843 2008-06-17 11:52 ********.rtf
-rwx------  1 ubuntu root 8286104 2008-06-19 10:57 opera_9.50.etch-qt3_i386.deb
-rwx------  1 ubuntu root  281435 2008-05-23 15:09 ********.JPG
-rwx------  1 ubuntu root  168781 2008-05-23 10:28 ********.JPG
-rwx------  1 ubuntu root   36510 2008-05-26 00:43 ********.jpg
-rwx------  1 ubuntu root   97280 2008-06-11 09:55 ********.doc
-rwx------  1 ubuntu root   28926 2008-06-18 07:31 ********.odt
-rwx------  1 ubuntu root    8244 2008-05-28 01:55 ********.odt
drwx------  2 ubuntu root   32768 2008-06-25 02:55 Recycled
-rwx------  1 ubuntu root   23780 2008-05-05 00:45 ********.odt
drwx------  2 ubuntu root   32768 2008-06-12 22:24 Skate Videos
-rwx------  1 ubuntu root     202 2008-04-26 06:48 sudu trick.desktop
drwx------  2 ubuntu root   32768 2008-06-25 02:55 System Volume Information
-rwx------  1 ubuntu root   28672 2008-06-24 18:51 Thumbs.db
drwx------ 70 ubuntu root   32768 2008-06-24 05:57 Torrents Downloads
drwx------  3 ubuntu root   32768 2008-06-25 02:55 .Trash-ubuntu
drwx------ 38 ubuntu root   32768 2007-12-07 14:03 TV Series
-rwx------  1 ubuntu root   98304 2008-06-13 00:42 ********.doc
drwx------  3 ubuntu root   32768 2008-06-24 08:24 untitled folder 2
drwx------  2 ubuntu root   32768 2008-04-22 01:24 WallpapersAd-6

ubuntu@ubuntu:/media/My Book$ ls -la .Trash-ubuntu/
total 96
drwx------  3 ubuntu root 32768 2008-06-25 02:55 .
drwx------ 14 ubuntu root 32768 1970-01-01 00:00 ..
drwx------  3 ubuntu root 32768 2008-06-24 13:21 Di151.Trash-ubuntu
ubuntu@ubuntu:/media/My Book$ 


I replaced file names with ******** 

The .Trash-ubuntu is showing up today because the Trash still has the stuff from the Recycled folder I tried to delete yesterday but it wouldn't let me, it says it's a read only disk.

---

### Post by Rocket2DMn on 2008-06-25
Yes, I read your post.
I'm not sure what "Di151.Trash-ubuntu" is exactly, though.  So it's mounting your USB drive as read only?
The easiest thing to do is to plug the drive back into windows, delete the entire .Trash-ubuntu folder, then empty the recycle bin.  Now check to make sure that it says there is empty space, then defragment the hard drive from within Windows (this can't be done in linux).  Again verify that there is free space, then safely remove the drive and plug it back into Ubuntu.
Is there free space now on the drive?  If not, please post the output of these commands:
```
df -h /media/"My Book"
sudo fdisk -l
mount
```
You can also show the size of folders using
```
du -h /media/"My Book" --max-depth=1
```

---

### Post by mrGRINCH on 2008-06-26
Okay so I defragmented the drive, it took like 10 hours. I deleted the trash folder. The external hard drive I use doesn't have a safe removal option, it's just plug and play, you can't "eject" it, it doesn't have the option under the menu. So I made sure it still said it had space which it does, I unplugged it and plug it back into my Ubuntu laptop but I still have the same problem, it says I only have 690MB of space instead of 14GB. 

Here is the output of your commands.

ubuntu@ubuntu:~$ df -h /media/"MY BOOK"
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             466G  465G  691M 100% /media/MY BOOK


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcdcfe52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14217   114198021   83  Linux
/dev/sda2           14218       14593     3020220    5  Extended
/dev/sda5           14218       14593     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /media/MY BOOK type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)

---

### Post by Rocket2DMn on 2008-06-27
I'm really at a loss as to why this is.  You can check the du command I listed to see which folder it is that is taking up so much space (and can change max depth or run it in each subfolder).  You may just have to check which folder(s) have the size discrepancy between Windows and Ubuntu.

---

