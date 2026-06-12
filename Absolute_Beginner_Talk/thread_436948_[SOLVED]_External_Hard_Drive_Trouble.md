---
title: "[SOLVED] External Hard Drive Trouble"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-08
I have an external 500 GB hard drive which i use for back up and stuff. It was NTFS, but I thought I'd make it EXT3 because I wanna be as Linux oriented as possible.
 
I have a dual boot with Ubuntu Feisty and Vista Premium.
Anyway, after I formatted it to EXT3, it has stopped being recognized as an external drive. Ubuntu says its /dev/sdb1. Vista says its Disk 1 (Disk 0 being my internal drive in the laptop).
 
1) I can mount it in Ubuntu, but if its not connected, i get a bunch of errors on boot up. My force checks on other drives fails with exit status 8 or 9 or 1
 
2) Vista sees the disk in Disk Management, but will not allow me to mount it. I do have FS-Driver installed in the Vista partition.
 
3) How can I make sure both OS'es see the drive as an external drive that it is !!
 
4) I am thinking (tell me if I am wrong), all external devices in Ubuntu should be under /media, correct? So why is Ubuntu seeing it in /dev/sdb1 ( as a slave drive )
 
 
Thanks for your help guys !

---

### Post by LaRoza on 2007-05-08
If it is formatted as EXT3, Vista won't be able to read it. For sharing, FAT32 is best. There is something for Windows that allows it to read EXT3, but I do not know what it is and if it work on Vista.

/dev means device. /media means external media, I don't know about external hard drives, but flash drives show up in both.

/dev/sda is a hard disk, Feisty calls all hard disks /sdx, I believe, other Ubuntu distros use /hdx too for non-SATA hard disks.

---

### Post by youthforlinux on 2007-05-08
I would re-format it as NTFS and install ntfs3g.  You can read/write to it better in Vista that way with little problem, and it will act just as good as a drive in ubuntu.

```
sudo aptitude install ntfs-config
```

Also Fat32 doesn't always work well with really large hard drives unless you split the hard drive into a lot of smaller partitions.

---

### Post by Inxsible on 2007-05-08
> **LaRoza said:**
> If it is formatted as EXT3, Vista won't be able to read it. For sharing, FAT32 is best. There is something for Windows that allows it to read EXT3, but I do not know what it is and if it work on Vista.
 
/dev means device. /media means external media, I don't know about external hard drives, but flash drives show up in both.
 
/dev/sda is a hard disk, Feisty calls all hard disks /sdx, I believe, other Ubuntu distros use /hdx too for non-SATA hard disks.
 
Vista can read EXT3 partitions with FS-Driver, like i mentioned before. In fact I have a partition on my internal drive which I share between Vista and Ubuntu.

---

### Post by Inxsible on 2007-05-08
> **youthforlinux said:**
> I would re-format it as NTFS and install ntfs3g. You can read/write to it better in Vista that way with little problem, and it will act just as good as a drive in ubuntu.
 
```
sudo aptitude install ntfs-config
```
 
Also Fat32 doesn't always work well with really large hard drives unless you split the hard drive into a lot of smaller partitions.
 
I already have NTFS-3G installed. But like I said, I was trying to be more Linux Oriented and also would like to get to the bottom of this problem

---

### Post by Inxsible on 2007-05-08
Bump. 
 
Someone........
 
 
Anyone.....

---

### Post by alchimera on 2007-05-08
> Anyway, after I formatted it to EXT3, it has stopped being recognized as an external drive. Ubuntu says its /dev/sdb1.
 
1) I can mount it in Ubuntu, but if its not connected, i get a bunch of errors on boot up. My force checks on other drives fails with exit status 8 or 9 or 1To get my Seagate to play pretty, i installed **pysdm **(use synaptic)**, **a storage device manager (that runs in python) and that sorted the mountpoints & options - well, after a few goes anyway...!

>  4) I am thinking (tell me if I am wrong), all external devices in Ubuntu should be under /media, correct? So why is Ubuntu seeing it in /dev/sdb1 ( as a slave drive )/media is where the *filesystem* is mounted,  so for example the device /dev/sdb1 can be mounted as a filesystem at /media/sdb1:

```
 sudo mount /dev/sdb1 /media/sdb1
```Sorry, i have no experience with Vista, but my XP has no trouble with ext3 using FSdrive.

---

### Post by Inxsible on 2007-05-09
I already have a mount point for the external drive.
 
Should I even have an auto-mount point for an external drive in the first place? i.e. Should I remove the entry from /etc/fstab ?
 
Because, I want it to mount only when I connect it, and not bother with looking for it when its not connected.
 
I really need to get this fixed !!
 
Any suggestions?

---

### Post by Inxsible on 2007-05-09
Bump again !

---

### Post by alchimera on 2007-05-09
> **Inxsible said:**
> Bump again !

is this any help?    [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

### Post by Inxsible on 2007-05-09
I came across the same thing by accident while trolling the forums. 
 
But thanks... I havent tried it yet as I am still at work :(

---

### Post by Terl on 2007-05-09
I would actually format it as NTFS.  That will make windows happy and Linux is more courteous and will work with NTFS.  Windows seems to whine more.  :) 

You are getting errors if it is not plugged in when you start Ubuntu because per fstab the drive is supposed to be there.  It is in Ubuntu's partition table.  I would not set it to auto-mount either since it seems that sometimes it is not connected.  I used to have a usb external and I would just mount it when I needed it available.

---

### Post by Inxsible on 2007-05-09
> **Terl said:**
> I would actually format it as NTFS. That will make windows happy and Linux is more courteous and will work with NTFS. Windows seems to whine more. :) 
 
You are getting errors if it is not plugged in when you start Ubuntu because per fstab the drive is supposed to be there. It is in Ubuntu's partition table. I would not set it to auto-mount either since it seems that sometimes it is not connected. I used to have a usb external and I would just mount it when I needed it available.
 
yeah, I guess its because I used 'mount' as opposed to 'pmount'. Maybe that's why Ubuntu thinks its an internal drive and not an external one.
 
Me wants to go home early from work....and try all that ;)

---

### Post by Terl on 2007-05-09
> **Inxsible said:**
> yeah, I guess its because I used 'mount' as opposed to 'pmount'. Maybe that's why Ubuntu thinks its an internal drive and not an external one.
 
Me wants to go home early from work....and try all that ;)

Hah hah.  I have been there before...wanting to go home and try something.  I have thought and thought about problems before and then the idea hits you and you can hardly wait to go so you can try your theory :)

I am working on some self learning of c++ and that also some shell scripting.  I keep thinking on that lots of times too.  In fact I am at work now :) :lolflag:

---

### Post by cotcot on 2007-05-09
> **LaRoza said:**
> If it is formatted as EXT3, Vista won't be able to read it. For sharing, FAT32 is best. There is something for Windows that allows it to read EXT3, but I do not know what it is and if it work on Vista.

/dev means device. /media means external media, I don't know about external hard drives, but flash drives show up in both.

/dev/sda is a hard disk, Feisty calls all hard disks /sdx, I believe, other Ubuntu distros use /hdx too for non-SATA hard disks.

The driver for windows XP to see EXT2/3 can be downloaded [here]("http://www.fs-driver.org/"). 
For Vista there seems to be [this]("http://ext2fsd.sourceforge.net/") solution. I cannot check it as I have no vista (and do not want vista)

---

### Post by dannyboy79 on 2007-05-12
> **cotcot said:**
> The driver for windows XP to see EXT2/3 can be downloaded [here]("http://www.fs-driver.org/"). 
For Vista there seems to be [this]("http://ext2fsd.sourceforge.net/") solution. I cannot check it as I have no vista (and do not want vista)
i have been sruggling with this! i have fiesty and I installed ntfs-3g and when I piug it in, it works just fine, I can write to it. but all of a sudden it will unmount and remount itself and then it keep happening? 

if you have an exernal drive you DON'T want to have an entry in your fstab and udev, hal, and or hotplug will handle it when it get's plugged in. the weird thinng is that after I plug it in and issue the mount command, it shows that the device is mounted with fuseblk and not ntfs-3g so I don't know what that's all about?

i have looked for other threads relating to external devices and ntfs-3g but I can't seem to find useful info, I noticed that for edgy, you had to build pmount using a version from givre's repo and I sent him a PM but he didn't respond yet. so I wonder if we need to build pmount so this works?

---

