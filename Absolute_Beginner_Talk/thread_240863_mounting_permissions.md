---
title: "mounting permissions"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by schreck494 on 2006-08-21
I successfully mounted a partition using:
```
sudo mkdir /media/harddrive
sudo mount /dev/hda2 /media/harddrive
```
The problem is that I can't write to the partiton.  The partition is formatted with fat32.  When I go under the permissions tab on the only boxes that are checked are the read boxes.  all of the other boxes are blank.  When I try to check the write box, I get:
Sorry, couldn't change the permissions of "14.6 GB Volume: harddrive".
What do I need to do?

---

### Post by Metacarpal on 2006-08-21
You'll need root access to change the read/write properties for the drive.
In Terminal, enter:
```
sudo nautilus
```
then enter your password when prompted.  Use the Nautilus window that opens up to change the permissions.

---

### Post by aysiu on 2006-08-21
You need to mount it properly: ```
sudo umount /media/harddrive
sudo mount -t vfat /dev/hda2 /media/harddrive -o iocharset=utf8,umask=0222
```

---

### Post by blackened on 2006-08-21
First do this:
```
sudo gedit /etc/fstab
```

Add this line:
```
/dev/hda2	/media/harddrive	vfat	rw,users	0	0
```

This should allow you to use the mount and umount commands without first issuing the sudo command a la

```
mount /media/harddrive
```

which, in turn, should mount the drive giving you read and write permissions.

---

### Post by aysiu on 2006-08-21
Instead of doing ```
sudo gedit /etc/fstab
``` do this instead ```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
``` The first command makes a backup copy of your fstab file, which is an important system file. The second command invokes *gksudo*, since you're using a graphical program. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by schreck494 on 2006-08-21
I edited fstab, but I still have to type in sudo to do commands, I don't know if that is part of the problem or not.  I tried all of the other things and they don't work.

---

### Post by taurus on 2006-08-21
Unmount it first and remount it with the right permissions...

```

sudo umount /media/harddrive
sudo mount -a

```

---

### Post by schreck494 on 2006-08-21
the mount -a doesnt help.

---

### Post by taurus on 2006-08-21
You mean the "sudo mount -a" command!  What does your /etc/fstab look like then?

```
more /etc/fstab
```

---

### Post by schreck494 on 2006-08-21
It looks like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


---

### Post by taurus on 2006-08-21
You need to edit your /etc/fstab 

```
gksudo gedit /etc/fstab
```
and add this line to the end of it...

```

/dev/hda2   /media/harddrive   vfat   defaults,umask=0000   0   0

```
Then, mount it again with

```
sudo mount -a
```

---

### Post by schreck494 on 2006-08-21
It still doesn't give me write permissions or execute permissions

---

### Post by taurus on 2006-08-21
Are you sure you have modified your /etc/fstab?  Can you post it here again???

---

### Post by schreck494 on 2006-08-21
the fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2   /media/harddrive   vfat   defaults,umask=0000   0   0

---

### Post by taurus on 2006-08-21
Run these two commands again...

```

sudo umount /dev/hda2
sudo mount -a

```

---

### Post by schreck494 on 2006-08-21
Permissions are still read only.  And I can't click a box to change it.

---

### Post by taurus on 2006-08-21
What is the output of this command then?

```
df
```
You cannot change permissions from clicking it for vfat or ntfs.  It has to be in /etc/fstab!

---

### Post by glorfindel_i510 on 2006-08-21
I'm having more or less the same problems schreck494 has described..

I would also like ubuntu to automatically mount the fat32 drive at startup and show it in the desktop...is that possible???

---

### Post by taurus on 2006-08-21
> **glorfindel_i510 said:**
> 
I would also like ubuntu to automatically mount the fat32 drive at startup and show it in the desktop...is that possible???
Yes, by including an entry in /etc/fstab and mount it on /media...

---

### Post by schreck494 on 2006-08-21
The output of df:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              8815404   2679148   5688448  33% /
varrun                  225648        88    225560   1% /var/run
varlock                 225648         4    225644   1% /var/lock
udev                    225648       120    225528   1% /dev
devshm                  225648         0    225648   0% /dev/shm
lrm                     225648     18856    206792   9% /lib/modules/2.6.15-23-386/volatile
/dev/hda2             15343136        88  15343048   1% /media/idedisk
/dev/hda2             15343136        88  15343048   1% /media/harddrive

---

### Post by taurus on 2006-08-21
Wait a second!  How come you mount /dev/hda2 on two difference places, /media/idedisk & /media/harddrive?????????????????????

Try to umount them both and mount it again using the entry from /etc/fstab!

```

sudo umount /media/idedisk /media/harddrive
sudo mount -a
df 

```

---

### Post by schreck494 on 2006-08-21
I still only have read permissions.  Here is the new df:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              8815404   2680172   5687424  33% /
varrun                  225648        88    225560   1% /var/run
varlock                 225648         4    225644   1% /var/lock
udev                    225648       120    225528   1% /dev
devshm                  225648         0    225648   0% /dev/shm
lrm                     225648     18856    206792   9% /lib/modules/2.6.15-23-386/volatile
/dev/hda2             15343136        88  15343048   1% /media/harddrive

---

### Post by taurus on 2006-08-21
And your /etc/fstab still looks good, right!!!

---

### Post by schreck494 on 2006-08-21
As far as I can tell it looks good, but that doesn't mean much.  Here it is for more knowledgeable people:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2   /media/harddrive   vfat   defaults,umask=0000   0   0


---

### Post by schreck494 on 2006-08-22
This is weird when I right click on the drive in computer it only shows read permissions.  But when I actually go into the drive I have all the permissions.  So my problem is fixed. :-D

---

### Post by taurus on 2006-08-22
> **schreck494 said:**
> This is weird when I right click on the drive in computer it only shows read permissions.  But when I actually go into the drive I have all the permissions.  So my problem is fixed. :-D
Then don't right click on the drive!!!  ;)

---

### Post by Gerriec on 2006-08-22
As a Newbie, I have been following this thread with great interest, and I have to ask this question ----

Is it possible for someone to lay out a straight forward procedure of how to mount and unmount a hard drive. ????????????

In this thread various advisors have given varying ways of doing it, ie. use fstab this way or that way, umask 0000 and umask 0222, use gedit or gkedit, I finish up not knowing which or what is correct.

Gerrie C.

---

### Post by taurus on 2006-08-22
To mount a drive, assuming it's /dev/hda1 with vfat/fat32 filesystem...

```

sudo mkdir /media/harddrive
sudo mount -t vfat /dev/hda1 /media/harddrive

```
To unmount it...

```

sudo umount /dev/hda1
-or-
sudo umount /media/harddrive

```

p.s.  You use "umask=0222" in /etc/fstab if you have NTFS since you can only read from it but you use "umask=0000" for vfat/fat32 filesystem so you can read and write to it...

---

### Post by Gerriec on 2006-08-22
**taurus** ---- Thank You, that I can understand. Now I will try it.

Regards =D> 

Gerrie C.

ps: If I dont come back you know I will have succeeded. Thank You

---

### Post by taurus on 2006-08-22
> **Gerriec said:**
> **taurus** ---- Thank You, that I can understand. Now I will try it.

Regards =D> 

Gerrie C.

ps: If I dont come back you know I will have succeeded. Thank You
Good luck and if you have problems with it, just PM me then.

---

