---
title: "Issues with FAT32"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Sou Portugues on 2007-02-05
So-
My second hard drive is a big ol 250gb sata drive.  I had partitioned it in gparted as fat32, but in Ubuntu, it wont let me mount it.  If I partition it in Ubuntu, I can mount it, but not dismount.  Furthermore, Ubuntu will only seem to let me partition it as ext2.  Either way I cut it, I cant write to the thing or change its partition via X (I dont want to start messing with it in terminal, I've pooched things up before with chmod 777).
So
What in da hey is going on here.
Whats the difference between fat and etx, and ext3 and ext2.

---

### Post by taurus on 2007-02-05
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Sou Portugues on 2007-02-05
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9587    77007546   83  Linux
/dev/sda2            9588        9964     3028252+   5  Extended
/dev/sda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706    b  W95 FAT32

Disk /dev/sdc: 163.9 GB, 163928605184 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19929   160079661    b  W95 FAT32

---

### Post by taurus on 2007-02-05
I assume you are talking about /dev/sdb1, 250GB.  Looks like it is fat32/vfat.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
You should be able to write to it, /media/sdb1, now.

---

### Post by Sou Portugues on 2007-02-05
Thank you- I'll give that a whirl.
While I have your ear, whats the difference between fat and ext, and ext2 and ext3?

---

### Post by closetpirate on 2007-02-05
!Wrong thread!

---

### Post by Sou Portugues on 2007-02-05
Hey Pirate-
YAR!!!
I'm a pirate to me hearty:) 
Actually, taurus got me going, I'm square. (Thanks you brave moderating soul you!)

But if anyone wants to educate me on the dfferences in file systems...

Actually, if you have a minute taurus, what the hey did I just do there???

---

### Post by taurus on 2007-02-05
Fat32 is an old Window filesystem which I don't think you should use anymore.  Ext2 is a Linux filesystem and ext3 is the same as ext2 except it has journal; it can handle your system before in case there are crashes.  And as far as I know, ext3 is the default filesystem for Ubuntu.

You can access your ext2/ext3 from Windows with this program, [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by Sou Portugues on 2007-02-14
So,
last night my system crashed after i updated the kernel, and for some reason, I couldn't even get the live cd to run.  I wiped my drives and re-installed, but now have a similar problem to what I was experiencing with the secondary sata drive (storage), only this time its ext3 instead of fat32.  
I cant mount the drive.  Here is what fstab tells me-

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9587    77007546   83  Linux
/dev/sda2            9588        9964     3028252+   5  Extended
/dev/sda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706   83  Linux

I tried tarus's instructions from 3 or so posts above. but to no avail (assumably because of different filesystems).

Thanks for the help lkast time, but if you folks could be so kind as to point me in the right direction again....

---

### Post by taurus on 2007-02-14
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```
Save it.  Now, create that new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
And if you want to have a write permission to /media/sdb1, then send me the output of this command from a terminal.

```
id
```

---

### Post by Sou Portugues on 2007-02-14
[QUOTE
And if you want to have a write permission to /media/sdb1, then send me the output of this command from a terminal.

```
id
```[/QUOTE]

uid=1000(zen) gid=1000(zen) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(zen)

---

### Post by taurus on 2007-02-14
```
sudo chown -R zen:zen /media/sdb1
ls -la /media
```

---

### Post by Sou Portugues on 2007-02-14
I think that did the trick, Thanks.
By the way, what is the lost and found folder in here (sdb1), and do I need it?

(I'll spare you the pain of explaining what all the code was having me do:wink: :)

---

### Post by taurus on 2007-02-14
The first line is to change the ownership of /media/sdb1 from root to zen so zen can write to /media/sdb1 anytime zen wants.

The second line is to list everything (with permissions and what not) under /media so you can now see that zen is the owner of sdb1.

There will always be lost+found directory for ext3 filesystem in case there is something wrong with the partition, it has somewhere to write the data to.  Therefore, I would leave it alone since it's not taking up any space right now.

---

### Post by Sou Portugues on 2007-02-14
Thanks man, I really appreciate your help.
While you were typing, I found a very good question over here, I wonder if you might shed some light on...

[http://www.ubuntuforums.org/showthread.php?t=361097](http://www.ubuntuforums.org/showthread.php?t=361097)

Basically, the question was, do new updates replace old ones (as in delete what they are replacing), or simply archive (as in amass until you run out of space)?

---

### Post by taurus on 2007-02-14
Yes, the new updates will replace the old ones on your system, removing the old programs.

---

### Post by Sou Portugues on 2007-02-14
Thanks

---

