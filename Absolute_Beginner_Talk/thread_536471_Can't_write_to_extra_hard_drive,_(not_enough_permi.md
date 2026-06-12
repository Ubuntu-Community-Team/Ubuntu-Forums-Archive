---
title: "Can't write to extra hard drive, (not enough permissions)"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by bertlacy on 2007-08-27
Hey all,

Heres is my problem...

I have a 350 GB Western Digital IDE hard drive as my Master that has my 'file system' on it.  This drive works great, no problems there.

I ALSO have a 250 GB Western Digital SATA hard drive installed.  I have my drivers installed, etc and the system can see the disk, the only problem is that I can't write to it.  The file path to it is /media/disk

Can someone help me so I can write/etc files to this drive...!

---

### Post by ddrichardson on 2007-08-27
Is it formatted as NTFS, in which case you need the ntfs-3g utils.

---

### Post by bertlacy on 2007-08-27
where can i find that out, under properties?

I will install that anyway and let you guy's know.

---

### Post by bertlacy on 2007-08-27
Well that didn't work, I only get the box to check 'write to external device' the 'write to internal device' is grayed out.

Its weird i know.

I can attach a screen shot if that would help???

---

### Post by ddrichardson on 2007-08-27
can you write to it as sudo?

---

### Post by bodhi.zazen on 2007-08-27
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

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by bertlacy on 2007-08-27
> **ddrichardson said:**
> can you write to it as sudo?

I can't write to it at all, there is a icon on the desktop for it, i can open it but that is it

---

### Post by bertlacy on 2007-08-27
> **bodhi.zazen said:**
> Mounting and permissions depends on the file system:

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

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]


THIS WORKED!!!

And I can't believe that all i needed to do was 'CHMOD' it, thanks guys!!!!

---

### Post by ddrichardson on 2007-08-27
What bodhi.zazen said. ;-)

---

