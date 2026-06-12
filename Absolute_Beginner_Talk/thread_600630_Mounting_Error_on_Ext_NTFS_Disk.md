---
title: "Mounting Error on Ext NTFS Disk"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Vega on 2007-11-02
[[IMG]http://img505.imageshack.us/img505/6981/mounterrorlf5.th.png[/IMG]](http://img505.imageshack.us/my.php?image=mounterrorlf5.png)

Seagate 320GB Free Agent

---

### Post by DavidJBerg on 2007-11-02
I had that some error message with my seagate external and followed choice 2 and it worked.

---

### Post by PmDematagoda on 2007-11-02
This is a bit of a messy fix, but it works, 

1) Open up Nautilus in su mode using "sudo nautilus"

2) Go to /media and create a new folder.

3) Close nautilus and using the same terminal input:-
```

sudo ntfs-3g /dev/pathofdrive /media/nameoffolder -o force
```

After you are finished, do:-
```

sudo umount /media/nameoffolder
```

---

### Post by Vega on 2007-11-04
> **PmDematagoda said:**
> This is a bit of a messy fix, but it works, 

1) Open up Nautilus in su mode using "sudo nautilus"

2) Go to /media and create a new folder.

3) Close nautilus and using the same terminal input:-
```

sudo ntfs-3g /dev/pathofdrive /media/nameoffolder -o force
```

After you are finished, do:-
```

sudo umount /media/nameoffolder
```



neh it doesn't work in terminal I keep getting 'volume not found
> enact@enact-desktop:~$ sudo ntfs-3g /dev/New Volume /media/New Volume -o force
ntfs-3g: You must specify exactly one device and exactly one mount point.

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org) 

man.. I wish NTFS 3G would work

---

### Post by PmDematagoda on 2007-11-05
Did you enable read/write support for external NTFS volumes? If you haven't, install ntfs-config using:-

```
sudo apt-get install ntfs-config
```

and then enable it in the NTFS Configuration Tool in Applications>System Tools.

---

