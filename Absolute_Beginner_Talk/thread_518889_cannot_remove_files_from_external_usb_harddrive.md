---
title: "cannot remove files from external usb harddrive"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by johnapeterson on 2007-08-06
Hello,
I got onto ubuntu last week.  I problem that I am having is with a external usb drive.  I can access file fine, but if I want to remove the file, the "move to trash" item is greyed out.  I moved some items from the old Windows system up to the ext HD to put onto ubuntu, got then onto the internal HD, but now I need to remove them from the external HD.

Thanks,
John

---

### Post by Rocket2DMn on 2007-08-06
What file system does the external HD use?  If you set it up with Windows XP, it probably runs ntfs (in which case you will need ntfs-3g).
Connect the drive and then please post the output of
```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by johnapeterson on 2007-08-06
Here is the results from that code input:

john@john-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14569   117025461   83  Linux
/dev/sda2           14570       14946     3028252+   5  Extended
/dev/sda5           14570       14946     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
john@john-desktop:~$ cat /etc/sources.list
cat: /etc/sources.list: No such file or directory
john@john-desktop:~$

---

### Post by Inxsible on 2007-08-06
you need to install ntfs-3g to have write access on NTFS drives.
Go to Applications -- > Add/Remove. Search for "ntfs" without quptes. Install NTFS Configuration Tool.

After Installation, Go to Applications --> System Tools --> NTFS Configuration Tool and enable write access to internal as well as external drives.

That should do it !

---

### Post by johnapeterson on 2007-08-06
OK,
Did what you said, but now it will say I can safely remove the drive, takes the icon off the desktop, but then it says it cannot eject the drive and puts it back on.

I am also still unable to move files from the external drive to the trash.

---

### Post by alienexplorers on 2007-08-06
First thing is to get your source list back, then make sure your external HD is mounted because you won't be able to do anything with it until it is.

---

### Post by Inxsible on 2007-08-06
do you own the mount point?

you can change ownership of the mount point to gain access like so

```
sudo chown -R <your username>:<your group> <path to the mount point>
```

---

### Post by Inxsible on 2007-08-06
it should be ```
/etc/apt/sources.list
``` But why do we need his sources.list ??

the only problem he has is with the usb drive.

did you(Rocket2Dmn) mean his fstab by any chance ? 

```
cat /etc/fstab
```

---

### Post by Rocket2DMn on 2007-08-07
> **Inxsible said:**
> it should be ```
/etc/apt/sources.list
``` But why do we need his sources.list ??

the only problem he has is with the usb drive.

did you(Rocket2Dmn) mean his fstab by any chance ? 

```
cat /etc/fstab
```

Hehe, I did indeed, thanks for catching that, I've changed the entry.

---

