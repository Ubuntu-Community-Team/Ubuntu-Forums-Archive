---
title: "Access Internal HDD"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by EricJosepi on 2007-03-20
Hello again,

I recently installed Edgy onto my External HDD and I switch between that and my native Windows XP install.  Recently though, Windows ate its own tail and I need to pull some files off the hard drive.  Problem is though, my internal HDD wasn't present in the install and it's not it doesn't show up in Ubuntu.

Does anyone know how I can access this Hard drive and save my valuable files before I run the God-forsaken "Restore DVD"?

---

### Post by taurus on 2007-03-20
You need to mount the harddrive where Windows is on before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
(l as in lower case letter l, not number 1.)

---

### Post by t4thfavor on 2007-03-20
The same thing is going on in here, Maybe it would be better to read it instead of having us type it all over again. :) 
[http://www.ubuntuforums.org/showthread.php?t=389150](http://www.ubuntuforums.org/showthread.php?t=389150)

---

### Post by KenSentMe on 2007-03-20
You need to mount the harddrive. More information on how to do that can be found on this wiki page: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) .

You need to know on what partition of the internal disc your windows was installed. You can use the following command to do this:

```

sudo fdisk -l

```

---

### Post by EricJosepi on 2007-03-20
> **taurus said:**
> You need to mount the harddrive where Windows is on before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
(l as in lower case letter l, not number 1.)

Well, I tip my hat to you sir as this seems to be what I'm looking for.  Here's the out put from sudo fdisk -l
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16970   136311493+   5  Extended
/dev/sda2           16971       30384   107747955   83  Linux
/dev/sda3           30385       30515     1052257+  82  Linux swap / Solaris
/dev/sda5               1       14360   115346637    7  HPFS/NTFS
/dev/sda6           14361       16970    20964793+   b  W95 FAT32
```

---

### Post by taurus on 2007-03-20
So you want to mount /dev/hda1.  From a terminal, Applications -> Accessories -> Terminal, edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```

---

### Post by EricJosepi on 2007-03-20
Thank you, sir.  This has worked perfectly.  Thank you for restoring my faith in the "community".

---

