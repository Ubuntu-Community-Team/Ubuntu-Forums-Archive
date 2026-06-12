---
title: "Copying photos"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Glugglug on 2007-08-27
Hi I'm new on here I went for Ubuntu as I have just had to install a new Motherboard and was told I could have problems getting OEM Windows XP activated after the hardware change so I have two systems running but I would like to try Ubuntu feisty 7.04 .

I have installed it twice once before I changed the Motherboard but it got corrupted and wouldn't boot .       The first time I plugged my camera in it found it and copied the photos and put them in a file but I tried again today and it finds the camera and downloads the files but I can't seem to save them and when I plugged the camera in a second time I found  the same files had been sent back to the camera so ended up with two copies of each photo on the camera can anyone tell me where I went wrong please.

---

### Post by aspen_dv on 2007-08-27
What the hell are your problem man? Windows, Ubuntu or Camera? I trying to understand the post here. 
OK, did you get Ubuntu Feisty installed? you have uhhh...what the heck, please try to clear up your question.

---

### Post by bodhi.zazen on 2007-08-27
> **aspen_dv said:**
> What the hell are your problem man? Windows, Ubuntu or Camera? I trying to understand the post here. 
OK, did you get Ubuntu Feisty installed? you have uhhh...what the heck, please try to clear up your question.

Be nice ....

Glugglug: please clarify the problem as I also do not understand. My guess is you are having problems with mounting and permissions :

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

---

