---
title: "I can't open my Local Disks"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Hashimi on 2007-02-28
I can't open my Other Locak disk except the one which Ubuntu is installed..what can i do.

I have all my files and e-books there..

---

### Post by bodhi.zazen on 2007-02-28
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

### Post by urk_nono on 2007-02-28
Local disks as in partitions?

---

### Post by Hashimi on 2007-02-28
when i doulbe click my local disks , it gives error that = Unable to mount the selected volume...???

And also when i enter this command in terminal it says :permission denied:

```

/dev/hda1  /media/windows  ntfs-3g  defaults  0  0

```

I am newbie sorry ..

---

### Post by bodhi.zazen on 2007-02-28
That line you posted goes into fstab, not the command line ;)

Take a look at the links I gave you ...

---

### Post by Hashimi on 2007-03-01
THanks i do that.. It is also explained in Help Documentations in Ubuntu.

---

