---
title: "[SOLVED] Copying folder to external hard drive"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-03-15
Hi, I've read the other threads concerning this but not sure if it's similar.  I have got Ubuntu 7.10 just as I want it and therefore I have copied my whole hard drive to /backup.tar.bz2.  I would now like to move this to an external hard drive (partitioned into three) incase anything crashes and then I can reinstall this directory.  The partition is /media/disk-1 with no directory or files in it (it is partitioned to 135GB).  I am new to Linux and am trying to learn command syntax, but I'm failing here!  Any help gratefully received!  Thank you.

---

### Post by DrScum on 2008-03-15
I am not sure if I understand you correctly. Do you want to copy a folder to an external hard drive? Or do you want to create an image of your harddrive that could be restored in case of trouble?
The former would be a drag and drop action (mount the external harddrive, open it through the file manager, open the folder with the subfolder to be saved and drag the subfolder to be saved to the window with the external harddrive).

To create an image  check out these links [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
[http://martybugs.net/linux/image.cgi](http://martybugs.net/linux/image.cgi)
[http://www.okmoore.com/imagedrive.html](http://www.okmoore.com/imagedrive.html)

---

### Post by kellemes on 2008-03-15
> **Berean said:**
> Hi, I've read the other threads concerning this but not sure if it's similar.  I have got Ubuntu 7.10 just as I want it and therefore I have copied my whole hard drive to /backup.tar.bz2.  I would now like to move this to an external hard drive (partitioned into three) incase anything crashes and then I can reinstall this directory.  The partition is /media/disk-1 with no directory or files in it (it is partitioned to 135GB).  I am new to Linux and am trying to learn command syntax, but I'm failing here!  Any help gratefully received!  Thank you.

You can do the following from terminal..
```
mv pathto/backup.tar.bz2 /media/disk-1
```
Depending on how you setup the disk you may need to get root-privileges while moving..
```
sudo mv pathto/backup.tar.bz2 /media/disk-1
```

Edit: If you need to copy this file instead of moving simply replace "mv" with "cp"

---

### Post by Berean on 2008-03-15
Hi, and thanks for your responses.  Just to be clear: I have made an image of my hard drive (if that means copying the contents of it) called /backup.tar.bz2 that I would like to move to an external hard drive (partitioned).  I could then restore this image should I lose/corrupt/delete any of the Ubuntu files that I have taken so long to get as I would like.  I have done as you suggested drscum, but got the following readout (you'll notice that I don't have a "pathto" but you'll see from what I've entered);

ian@ian-laptop:~$ sudo mv pathto/backup.tar.bz2 /media/disk-1
[sudo] password for ian:
mv: cannot stat `pathto/backup.tar.bz2': No such file or directory
ian@ian-laptop:~$ sudo mv /backup.tar.bz2 /media/disk-1
mv: cannot create regular file `/media/disk-1/backup.tar.bz2': Read-only file system

Any help offered?  Many thanks.

---

### Post by Berean on 2008-03-15
Sorry, it was _your_ advice kellemes.  Thank you.  Does this make things clear DrScum?

---

### Post by taurus on 2008-03-15
What filesystem is your external drive, 135GB?  Is it ntfs?

```
sudp fdisk -l
```

---

### Post by Berean on 2008-03-15
Hi Taurus,

An external hard drive of 250 GB partitioned as follows;

ian@ian-laptop:~$ sudo fdisk -l
[sudo] password for ian:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d7f5ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        9541    76638051   83  Linux
/dev/sda3            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris
ian@ian-laptop:~$ 

Is this listing my external hard drive?  The partition I wish to copy the file to is 135GB, and my INTERNAL hard drive is reported to be 80GB but is more like 76GB.  Is this any help?

---

### Post by taurus on 2008-03-15
I don't see the list of your external drive at all!  Are you sure it's plugged it?  What about the output of this command since you said that it's mounted to /media/disk?

```
df -h
```

---

### Post by Berean on 2008-03-15
Definitely plugged in!  Listed as; disk, disk-1 and disk-2 which are all separate on my desktop but relate to the external hard drive.  Each one has the files on it I would expect.  The following is the readout from terminal;

ian@ian-laptop:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              72G   65G  5.1G  93% /
varrun                252M  124K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   80K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1              79G   25G   54G  32% /media/disk
/dev/sdb2             136G   33M  136G   1% /media/disk-1
/dev/sdb3              20G  7.1G   13G  37% /media/disk-2
ian@ian-laptop:/$ 

Is this what you'd expect?

---

### Post by taurus on 2008-03-15
Are are the filesystems for those three partitions on your external drive, /dev/sdb1, /dev/sdb2, & /dev/sdb3?

```
mount
```

---

### Post by Berean on 2008-03-15
Yes! Sorry for the delay: my system crashed.  It would appear that I have 55% of my80GB (read 76GB) hard drive in use and it was saying 100% of disk space used up after copying /backup.tar.bz2).  I have had to delete the image (/backup.tar.bz2) so now have enough disk space again.

ian@ian-laptop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sdb2 on /media/disk-1 type reiserfs (rw,nosuid,nodev)
/dev/sdb3 on /media/disk-2 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
ian@ian-laptop:~$ 

Is there a method of copying the whole of my hard drive to an external hard drive partition?  This would undoubtedly make things easier!

---

### Post by Berean on 2008-03-15
Anybody able to help?

---

### Post by DrScum on 2008-03-15
Berean, to have the image on the external harddrive is only half of the task. You have to have a method to restore it in case something goes wrong. However, I guess you know how to go about that.
To copy the image, do as I say above, you realize instantly that I am the point and click guy since I switched from the Redmont camp a while ago. However, I don't think that there is anything wrong with that.
So here again: just connect your external drive via the USB port. If you do that chances are that the drive is mounted automatically. Then just open the folder or subfolder you'd like to have your image stored in in a file manager window. Open the the folder with your image file in another file manager window and drag it to the external harddrive.
For the whole of your harddrive act in an analogue way for each folder (hope there are not too many) but just to be clear: copying the whole of your harddrive is not the same as having an image.

---

### Post by Berean on 2008-03-15
DrScum, thanks for responding again.  I've followed this thread ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)) and tried to make an image.  HOWEVER, it stops before finishing copying everything because my internal hard drive is full.  Even with compression.  Secondly, even with what I have copied I can't get the whole folder to move, saying I don't have permission when clearly I do!  I'm so impressed with Ubuntu, but this is driving me mad: it's taken over three weeks to try to get this right.  Can I not just copy the whole hard drive to an external hard drive with partition?  I really appreciate your help.

---

### Post by DrScum on 2008-03-17
Well, I don't really understand the part where you say: "I can't get the whole folder to move, saying I don't have permission, when clearly I do!" I assume, what you mean is: "I can't get the whole folder to copy".
I am not the Linux expert, I switched about a year ago from WinXP to Ubuntu. Thus I can't give you the details about permissions but I assume you have to be logged in as root if you want to copy the whole system folder. If you don't have generated a root user during install, I think you would have to do that first.
Secondly I think you should try to create an image again as you already did and use your external harddrive as a target right away. The link you are mentioning actually describes how you would do that: you navigate to your external drive to the directory where you would your TAR file to be located and then start the backup. That way you won't run into the problem that you internal harddrive doesn't have enough room.
A third suggestion would be to boot from a live CD (I suggest Damned Small Linux or Knoppix) and try copying the whole system that way. But keep in mind: I think just copying the system won't let you restore it in case of system failure.

---

### Post by Berean on 2008-03-17
Thanks guys for all your help.  I've gone with partimage and have successfully copied from my hard drive to an external hard drive, having made an image.  I appreciate all of the advice.  Regards.

---

