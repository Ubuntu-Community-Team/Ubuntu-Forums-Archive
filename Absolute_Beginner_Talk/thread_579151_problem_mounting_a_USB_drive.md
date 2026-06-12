---
title: "problem mounting a USB drive"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mrufino1 on 2007-10-18
Hi, This is my first post here and I am very much a beginner working very slowly through by ubuntu for beginners book. I am using ubuntu fairly well, with help from a friend and info I am finding on here. I am having a bit of difficulty with a problem mounting my USB drive however. I have a 2.5" external USB2 drive. It was mounting and an icon was showing up on the desktop anytime I would plug it in. I could write to it, read from it, etc. However, whenever I clicked eject it said it could not eject the disk. So I reformatted it, and then it wouldn't mount at all. I have reformatted it in the gnome partition manager, as FAT32, then ext3, now FAT32 again. I can mount the disk and unmount it from the command line by typing sudo mount -t vfat -o umask=000 /dev/sda1 /media/sda1 .
 When I try to have it auto mount by just plugging it in, I get the following error:
Cannot Mount Volume
Unable to Mount the Volume
mount_point cannot contain the following characters:
newline, G_DIR_SEPERATOR (usually /)

I am not sure what this means, I believe I set the mount point to media/sda1 by what I typed, right? I appreciate any insight, hopefully it is just something simple that I am doing wrong.

---

### Post by sheshbabu on 2007-10-18
How big is it? is it lesser than 2GB?

---

### Post by mrufino1 on 2007-10-18
60gb- it is a laptop drive in an enclosure. I should also add that I have searched for the answer and was not able to find one that referred specifically to the error I was getting. As I said, I can mount it manually through the command line, just not automatically, which I would prefer.

---

### Post by Inxsible on 2007-10-18
use pmount to mount it. Use my signature to find a small howto

---

### Post by mrufino1 on 2007-10-18
Hi, Thank you, unfortunately that is not doing what I am asking. I want to be able to plug in the drive and have it show up on the desktop, which did happen at one point, but it would not eject. I am very new to linux, with no unix  or programming experience at all, so there is something I am not understanding I am sure, but this does work with any removeable media that I use, including my mp3 player (4 gb creative muvo2) which shows up as a hard drive and ejects with no problem. I am able to mount and unmount the drive from the command line using the commands I typed in my original post (which I got straight from the ubuntu for beginners book, just using my filenames), but I don't want to have to do this every time if at all possible. The pmount command mounted the drive once, but it said I don't have permission to see the files (I am not yet understanding the permission thing but am continuing my reading). Now, when I type that, I do not see it open on the desktop, however I can access the files on the disk through the terminal, so obviously it is mounting. What am I missing? Thanks for the help and replies so far.

---

### Post by Inxsible on 2007-10-18
> **mrufino1 said:**
> Hi, Thank you, unfortunately that is not doing what I am asking. I want to be able to plug in the drive and have it show up on the desktop, which did happen at one point, but it would not eject.
If you mount it under /media, it will show up on your desktop. If you mount it anywhere else, it wont.

---

### Post by Inxsible on 2007-10-18
As for the permissions you can assume ownership of the mount point by 
```
sudo chown -R <your username>:<your group> <path to mount point>
```

---

### Post by mrufino1 on 2007-10-18
Sorry for being such a pain! Okay, so I typed sudo chown -R mark:mark /media/mark60, I get the next command line, but I still am not able to access the drive. Then I typed sudo chown -R mark:mark-laptop /media/mark60, and it says no such group- my username is mark, the command prompt says mark@mark-laptop, is mark-laptop my group? As for permissions, is there a way to make it so you can access whatever you need? I am not sure what is meant by making yourself root, aside form typing su or sudo in the command line. Thanks-Mark

EDIT: When I type mark:mark as username and group, I don't get an error but it doesn't seem to do anything. What is puzzling me is that if I mount the disk manually by typing sudo mount -t vfat -o umask=000 /dev/sda1 /media/sda1 then everything works fine, I just have to unmount from the command line as well. Maybe I should just memorize that line and do it since it works, but I am naturally inquisitive and pushy...

---

### Post by Inxsible on 2007-10-18
are you mounting it at /media/mark60?

you need to own the mount point, but make sure you have mounted the drive at that place first.

I ask, because in your example you are mounting at /media/sda1

---

### Post by mrufino1 on 2007-10-18
Thanks so much for your help so far first of all. I mounted it at /media/sda1. I realized it is not called mark60 anymore since I reformatted it, but the directory for mark60 was still there (I couldn't delete it). I had the bright idea of setting ownership of /media, was that a good idea? I was able to delete the newdisk and mark60 directories that I had set up when follwing previous instructions from my book. As I said, if I mount from the command line, by typing sudo mount -t vfat -o umask=000 /dev/sda1 /media/sda1 then everything works great, the icon shows up on the desktop, I can read and write, and I can unmount manually. If that is what I have to do for now to get it to work then I will, I just want to see if there is a way to have it work automatically. I would also love ot know what the heck that line I am typing actually means! Once I have it mounted, is there some setting to change that makes it automount? Remember, I am two weeks into ubuntu after being a windows guy forever- wizards and automated processes were a way of life for me!Still need windows for my music work(for now...), but  I really love using ubuntu, not only is it liberating but it runs really well and I will eventually understand how the innards work...

---

### Post by Inxsible on 2007-10-18
pmount is real easy if you use it correctly.

you can also auto-mount using the command line but you need to modify the entry for that drive in the fstab.

Generally, external drives are mounted with pmount, because it will mount your drive under /media automatically and also get you the icon on the desktop.

post the output of ```
sudo fdisk -l
``` -l is lowercase L. and ```
cat /etc/fstab
``` and i will give you the exact command so that your drive will automount. Also indicate which drive it is.

---

### Post by mrufino1 on 2007-10-18
Thanks, here is the text, copied and pasted:


mark@mark-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2187    17567046    7  HPFS/NTFS
/dev/hda2            4282        9729    43761060    f  W95 Ext'd (LBA)
/dev/hda3            2188        4281    16820055   83  Linux
/dev/hda5            4375        9729    43014006    b  W95 FAT32
/dev/hda6            4282        4374      746959+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7296    58605088+   b  W95 FAT32

mark@mark-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=4d2fbfab-b70d-4dad-be57-a10f266f3456 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=26EC8B40EC8B08EF /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=46FA-DB27  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=0b751cfe-f148-4e6f-abd8-b099ab4e054d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
mark@mark-laptop:~$

---

### Post by Inxsible on 2007-10-18
I am assuming you want to mount the sda1 which is 60GB.

```
sudo pmount /dev/sda1 mark60
```
This will mount the drive at /media/mark60, you can choose any other name. Make sure, however, that the folder does NOT already exist. pmount creates the folder for you and will not work if the folder already exists under /media

---

### Post by mrufino1 on 2007-10-18
This automounts it or I need to type this in each time I want to mount the drive? And how do I unmount if I do it like this? I'm going to try it now.

---

### Post by Inxsible on 2007-10-18
yes it will automount everytime. to unmount you need to right click the drive and click unmount or eject.

---

### Post by mrufino1 on 2007-10-18
It is not showing up on the desktop. In the filesystem, in the media folder, mark60 folder, it is locked and I don't have permission to access it either. Once this is made, do I need to do the own command? Still, when I just did that, I still can't access it, still locked and still not accessible. I typed sudo chown -R mark:mark /media/mark60 .That is what I am supposed to type there, right?

EDIT: I installed pmount from the package manager before- was I supposed to install the other two files that came up with the pmount search as well?

---

### Post by Inxsible on 2007-10-18
if mark60 folder was already there before you tried pmount, then it wont work. use a different folder name and see if it mounts. Of course, if its a permission issue, that can be fixed. First get it to mount.

use a folder name like MyDrive or something.

---

### Post by mrufino1 on 2007-10-18
I used mydrive, still no desktop icon, and the mydrive folder still shows up as locked in the browser. Maybe pmount is not installed correctly?

---

### Post by mrufino1 on 2007-10-18
To answer my own question, pmount was reinstalled, same thing is still happening. Is it possible that I need to enable permission for /dev/sda1? It is coming up that I don't have permission to access the parent folder. Anyway, still no desktop icon, which does appear and everything works fine when I mount manually.

---

### Post by mrufino1 on 2007-10-18
Just to clarify, the issue is not yet solved, I don't know if I made it sound that way. I appreciate the efforts so far.

---

