---
title: "How can I mount my partitions in Ubuntu i386"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by TR3GO on 2007-02-11
Hello,

         I recently had to reinstall Ubuntu and my first installation went great it even showed all my partitions on the desktop so I didn't have to mount them, and I could move the files from my other partitions over to my Ubuntu partition.

        Now since I had to reinstall my partitions aren't on the desktop anymore, and I tried mounting them by reading tutorials and I can't seem to get it right. Can anyone assist me in this process?

Here is my fstab:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc5     /media/windows     ntfs-fuse     auto,gid=1001,umask=0002 0 0
# /dev/hda1     /media/windows     ntfs-fuse     auto,gid=1001,umask=0002 0 0  $
# /dev/hda5     /media/windows     ntfs-fuse     auto,gid=1001,umask=0002 0 0  $
# /dev/hdc1     /media/windows     ntfs-fuse     auto,gid=1001,umask=0002 0 0  $
# /dev/hdc2     /media/windows     ntfs-fuse     auto,gid=1001,umask=0002 0 0
# /dev/hdc3     /media/wincows     ntfs-fuse     auto,gid=1001,umask=0002 0 0

UUID=6368746f-2074-616b-6f65-207575696400 /               ext2    defaults,erro$
# /dev/hdc6
UUID=0d7ebb6f-f820-413d-9e4f-a103b28e2699 none            swap    sw           $
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

[/B]

THANKS!!!:D
-Stefan

---

### Post by taurus on 2007-02-11
Why are you mounting all of your Windows partitions to a same mount point, /media/windows?

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by teaker1s on 2007-02-11
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

has sections on mounting etc

---

### Post by TR3GO on 2007-02-11
I'm not mounting all of my "WINDOWS" partitions. Sorry if I said that, what I want to do is that I have ONE Windows partition, and others like an MP3s partition, Video, Documents, etc. So I want them all visible on my desktop so I can watch Diggnation, listen to music, etc.

[B]
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825        9729    47431912+   f  W95 Ext'd (LBA)
/dev/hda5            3825        7648    30716248+   7  HPFS/NTFS
/dev/hda6            7649        9728    16707568+   7  HPFS/NTFS
/dev/hda7            9729        9729        8001   83  Linux

Disk /dev/hdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        3187    25599546    7  HPFS/NTFS
/dev/hdc2            3188        3309      979965    7  HPFS/NTFS
/dev/hdc3            3310        6374    24619612+   7  HPFS/NTFS
/dev/hdc4            6375       10011    29214202+   5  Extended
/dev/hdc5   *        6375        9945    28684026   83  Linux
/dev/hdc6            9946       10011      530113+  82  Linux swap / Solaris
[/B]

---

### Post by taurus on 2007-02-11
You have a bunch of them so which one do you want to mount?

---

### Post by TR3GO on 2007-02-11
I would like to mount all of them, and then I will view the contents of the paritions and unmount them if I don't need em. Yes a lot is right haha

---

### Post by teaker1s on 2007-02-11
Okay two ways I can think of
1) works in feisty but may or may not work in previous ubuntu versions
click on desktop panel and "add to panel" select "disk mounter". partitions then show up and can be mounted and opened with disc mounter
2)[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")
you can mount to a folder-now I have never tried ths but assuming you created a folder on desktop you could use it as a mount point. If not you could link to /media/windows from desktop.

---

### Post by taurus on 2007-02-11
```
gksudo gedit /etc/fstab
```
And add these lines at the end.

```

/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222 0 0
/dev/hda5   /media/hda5   ntfs   nls=utf8,umask=0222 0 0
/dev/hda6   /media/hda6   ntfs   nls=utf8,umask=0222 0 0
/dev/hdc1   /media/hdc1   ntfs   nls=utf8,umask=0222 0 0
/dev/hdc2   /media/hdc2   ntfs   nls=utf8,umask=0222 0 0
/dev/hdc3   /media/hdc3   ntfs   nls=utf8,umask=0222 0 0

```
Save the changes and create the new mount points and mount them all.

```
sudo mkdir /media/hda1 /media/hda5 /media/hda6 /media/hdc1 /media/hdc2 /media/hdc3
sudo mount -a
df -h
```

---

### Post by TR3GO on 2007-02-11
Ok AWESOME! Thanks guys I appreciate the help. I just have 2 further simple questions for ya.

1. How can I in windows terms (sorry :-( ) "create a shortcut" to these hda & hdc directories which are in my "/media/(partitions)" to my desktop?

2. How can I rename these files to like (music, documents, etc.)?

I appreciate the help!
-Stefan

---

### Post by teaker1s on 2007-02-11
go to the folder you want to link, right click and select make link.
cut and paste to desktop

---

### Post by TR3GO on 2007-02-11
That isn't an option for me, its a low opacity. And there aren't any other ways to do it through a right click.

---

### Post by derekr44 on 2007-02-11
I followed the excellent instructions above and successfully mounted my NTFS partition.

I tried doing the same for a spare NTFS drive by doing the following:

```
gksudo gedit /etc/fstab
/dev/hdb1   	/media/hdb1   	ntfs   nls=utf8,umask=0222 0 0
```

I created the directory for hdb1, but when I "sudo mount -a" I get an error.
[B]
mount: mount point /media/hdb1 does not exist[/B]

I'm a linux noob and would appreciate any help.  Thanks!

---

### Post by taurus on 2007-02-11
> **derekr44 said:**
> I followed the excellent instructions above and successfully mounted my NTFS partition.

I tried doing the same for a spare NTFS drive by doing the following:

```
gksudo gedit /etc/fstab
/dev/hdb1   	/media/hdb1   	ntfs   nls=utf8,umask=0222 0 0
```

I created the directory for hdb1, but when I "sudo mount -a" I get an error.
[B]
mount: mount point /media/hdb1 does not exist[/B]

I'm a linux noob and would appreciate any help.  Thanks!

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by derekr44 on 2007-02-11
Thank you, Taurus.  I could have sworn that directory was already there...

---

