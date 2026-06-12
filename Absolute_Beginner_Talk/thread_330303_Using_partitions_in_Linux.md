---
title: "Using partitions in Linux"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Curt101010 on 2007-01-02
Ok, this is a total noob question, but here it goes... I have an extra ext3 partition that is was created after Ubuntu was installed (used to be a NTFS partition).  How do I get Ubuntu to use that partition.  I'm used to Windows where you tell it physically where to put the file.  

Thanks in advance!!

---

### Post by Curt101010 on 2007-01-03
Hmmm.... OK, did I not explain my question well enough to be understood?  I'm sure this is an easy answer for all of you in the know.  I just want to make sure that I can use all of the space that I've allocated.

Thanks!

---

### Post by bartbes on 2007-01-03
You first have to know where it's mounted. So open up a console and type in:
```

mount

```
if you don't know which partition is mounted where, the numbering starts at hda1 (first HDD first partition), hda2 is first HDD second partition, and hdb1 is second HDD first partition, etc.
If you know where it is mounted, just save it in that directory, and it's on the disk!

---

### Post by Sef on 2007-01-03
OOps.

---

### Post by MiCovran on 2007-01-03
If you use "mount", you will have to be root to write files on it: ```
gksudo nautilus
```
My advice is to use "pmount" instead, it allows a normal user to read/write files. You just need to add your device to ```
/etc/pmount.allow
```
you can find your partition's name with: (it lists all of your partitions and their locations) ```
sudo fdisk -l
```

Now, for example, if your partition is: "/dev/hda8", you would type: ```
gksudo gedit /etc/pmount.allow
``` to open the "pmount.allow" and add a new line in it: ```
/dev/hda8
```
Close the text editor and save your changes. You can now mount your partition any time with: ```
pmount /dev/hda8 some_name
```
and you can find it at "/media/some_name/" (write something to identify your partition instead of *some-name*).
It looks kind of confusing, I know, but it's not really. You just need to get used to typing what you want to do, not clicking. If you want to mount it automatically on login, add this "pmount /dev/hda8/ some_name" to your startup programs list.

If you need some explanations, just ask. I had the same problem, I know how you feel. ;)

---

### Post by Bartender on 2007-01-03
Curt - 
Do you have plans for that partition, or do you just want to vaporize it and move the unallocated space into the main ext3 partition?

How big is it?  If you already have an ext3 partition sitting there unused and it's at least - oh, I don't know - 10GB, you might want to put another distro there!

---

### Post by bodhi.zazen on 2007-01-03
Mounting and permissions depends on the file system:

_Windows:_

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by raul_ on 2007-01-03
I would just format it and then resize the main partition with Gparted and the LiveCD ;)

---

### Post by Curt101010 on 2007-01-03
> **Bartender said:**
> Curt - 
Do you have plans for that partition, or do you just want to vaporize it and move the unallocated space into the main ext3 partition?

How big is it?  If you already have an ext3 partition sitting there unused and it's at least - oh, I don't know - 10GB, you might want to put another distro there!

It is +90 MB.  I'm not interested in installing another distro.  I want to use the space for file storage and manipulation.

I would love to vaporize it and reallocate the space, however, that part is in the front of the disk, and when I boot to the Ubuntu install disk and try to reallocate, it won't let me resize the back partition (where Ubuntu is installed).  :-(

---

### Post by Curt101010 on 2007-01-03
Thanks to everyone for their responses.  When I get home tonight, I'm going to try them out!!

---

### Post by Curt101010 on 2007-01-03
> **MiCovran said:**
> If you use "mount", you will have to be root to write files on it: ```
gksudo nautilus
```
My advice is to use "pmount" instead, it allows a normal user to read/write files. You just need to add your device to ```
/etc/pmount.allow
```
you can find your partition's name with: (it lists all of your partitions and their locations) ```
sudo fdisk -l
```

Now, for example, if your partition is: "/dev/hda8", you would type: ```
gksudo gedit /etc/pmount.allow
``` to open the "pmount.allow" and add a new line in it: ```
/dev/hda8
```
Close the text editor and save your changes. You can now mount your partition any time with: ```
pmount /dev/hda8 some_name
```
and you can find it at "/media/some_name/" (write something to identify your partition instead of *some-name*).
It looks kind of confusing, I know, but it's not really. You just need to get used to typing what you want to do, not clicking. 

Thanks!!  That worked just like you said it would.  :KS 

[QUOTE=MiCovran]If you want to mount it automatically on login, add this "pmount /dev/hda8/ some_name" to your startup programs list.
[/QUOTE]

Ok, so where is the startup programs list located and how do I edit it? ](*,)

---

### Post by raul_ on 2007-01-03
in Gnome:

System->Preferences->Sessions->Startup Programs

---

### Post by Curt101010 on 2007-01-03
> **raul_ said:**
> in Gnome:

System->Preferences->Sessions->Startup Programs

Sweet!  Thanks!!  :cool:

---

### Post by Curt101010 on 2007-01-04
> **bodhi.zazen said:**
> Mounting and permissions depends on the file system:

_Windows:_

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

Wow!!!  That was some amazing information.  And, unfortunatly, most of it went over my head.  I've read a lot of those links you listed, and plan on going back and reading the rest.  Great info there!!

---

