---
title: "Mounting the Mount"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by SoulRaver on 2007-10-23
:lolflag:

Ok so this is what I want to accomplish:

Running 7.10 on a old reused box. Just physically added an additional PATA drive (Slave settings on primary IDE channel). Aim is to make new space for my current configuration and the specific folder of /var/ftp


So what I done this far:
Plugged it in, isntalled 'qtparted' and made a 'ext3' partition of it. 

The mount got me stomped...



Anyone wanna bail out a noobie?

---

### Post by Pumalite on 2007-10-23
Post:
sudo fdisk -lu

---

### Post by SoulRaver on 2007-10-24
Thx Pumalite.

Now for the next part:
Do I link /var/ftp to hdb or move /var/flp to hdb? Or is there any real difference?

---

### Post by SoulRaver on 2007-10-31
Anyone?

---

### Post by taurus on 2007-10-31
You want to mount it through /etc/fstab so it will be mount automatically each time you boot.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /var/ftp   ext3   defaults   0   1
```
Save the change.  Then, create a new mount point if you haven't done so and mount it.

```
sudo mkdir /var/ftp
sudo mount -a
df -h
```

---

### Post by SoulRaver on 2007-11-01
Cheers Taurus! That did it.



Have a few questions here, just curios

I understand that this way the new HD is 'linked' (!?) to /var/ftp. Did I understand this correctly?
If so there is no performance issues here at all?

Had to 'sudo nano /etc/fstab' instead, guess that was a pure choice of sofware flavour. fstab is the file system table. Got that. 
The line 'dev/hdb1   /var/ftp   ext3   defaults   0   1' added the new HD and it's mount point to the default bootable filesystem?

'sudo mkdir /var/ftp' I replaced with 'cd /var/ftp' since the folder existed

'sudo mount -a' I presume flushed/reloaded the new fstab?

'df -h' gave a list of HD's




Did I interprit all that ok?

---

### Post by taurus on 2007-11-01
Perfect.

---

### Post by bluetec on 2007-11-01
as a very newbie, i have a little problem,
I was installing Gutsy (If this means Ubuntu 7.10), and it is my first experience ever with linux, on a hard drive that already contains Vista on it, so i left the "C" drive as it is (NTFS) for Vista, i made a root with mount point "/" and a swap partition and another partition with FAT32 filesystem.
The problem is that i choosed /Vista as a mount point (not /media/Vista) for the Vista drive , and I also choosed /Data for the other partition. now i can only find these two partitions as FOLDERS in the File System drive.

Now i want to change the mount point for both partitions to be able to see them as drives (change them to /media/DriveLable), Is it possible to do so with reformatting partitions or reinstalling ubuntu??

---

### Post by taurus on 2007-11-01
> **bluetec said:**
> as a very newbie, i have a little problem,
I was installing Gutsy (If this means Ubuntu 7.10), and it is my first experience ever with linux, on a hard drive that already contains Vista on it, so i left the "C" drive as it is (NTFS) for Vista, i made a root with mount point "/" and a swap partition and another partition with FAT32 filesystem.
The problem is that i choosed /Vista as a mount point (not /media/Vista) for the Vista drive , and I also choosed /Data for the other partition. now i can only find these two partitions as FOLDERS in the File System drive.

Now i want to change the mount point for both partitions to be able to see them as drives (change them to /media/DriveLable), Is it possible to do so with reformatting partitions or reinstalling ubuntu??

It is possible and doable.

Open a terminal, Applications -> Accessories -> Terminal, and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
Replace /vista with** /media/Vista** and /Data with **/media/DriveLable**.  Save the changes.

Now, you need to create those two new mount points to mount them to.

```
sudo mkdir /media/Vista /media/DriveLable
```
Reboot and you should see two icons on your desktop, one for Vista and one for your fat32 partition.

---

### Post by bluetec on 2007-11-02
wow, i'll be happy if it is that simple...
I will try it and come back to you
Thank you very much taurus

---

