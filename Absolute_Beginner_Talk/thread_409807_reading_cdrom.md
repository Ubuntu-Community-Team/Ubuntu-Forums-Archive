---
title: "reading cdrom"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by ottawa on 2007-04-15
Hello all,

I have the server 6.10 installed (newbie), I am able to walk the directory tree with the command cd and listing the files with the command ls.

If I understand it correctly, the cdrom drive is just a directory under linux located at /cdrom

If I cd from the root to /cdrom I am in the cdrom folder. Executing  ls  is not showing any folder/files which are on the cd inside of the cdrom DRIVE. 
All folders under root are marked blue, except cdrom, initrd.img and vmlinuz. What does this mean ? :confused: 

The cd is burned on a windows machine. Is that a problem ? It shouldn't be, or ?
What could be the problem, as Ubuntu is able to read the install cd.

---

### Post by Sef on 2007-04-15
> 
The cd is burned on a windows machine. Is that a problem ? It shouldn't be, or ?
What could be the problem, as Ubuntu is able to read the install cd.


1) What did you burn?

2) What format did you burn it in?

3) Will it work in Windows?

---

### Post by JTux on 2007-04-15
Maybe you have to mount the CD first in the server edition.

just try

```
mount /cdrom
```

or 

```
mount /media/cdrom
```

---

### Post by BoneKracker on 2007-04-15
On the server version, the way it comes installed (lean and secure), you have to mount disks manually (unless they are among those you specified to be automounted at boot).  This goes for cdroms, floppys, usbdisks, keydrives, etc. as well.

Basically, the reason there's nothing in /cdrom is that it's not mounted yet.

Blue items are directories (folders).
Light blue are symlinks (shortcuts).

The /cdrom you're looking at is probably a symlink to /mnt/cdrom.

You can check by doing an ls -l
```

cd /
ls -l
```

To mount it, try:```

sudo mount /mnt/cdrom
```

If that doesn't work, take a look at your /etc/fstab file to see what mount point it is set for.
```
less /etc/fstab
```
(e.g., it might be /media/cdrom)  

Then check if you can see your files.

If it's not in fstab, let us know.

---

