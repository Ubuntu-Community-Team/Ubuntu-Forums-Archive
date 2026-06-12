---
title: "Changing / Renaming mount points"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-07-31
I have 3 partitions...XP, Vista, Ubuntu.

What I boot into Ubuntu I can see the Vista partition is mounted but the XP partition doesn't appear to be.

Anyone got an answer/suggestions?

Also, I just created a new partition as a shared space for the 3 OS's (fat32).  How do I make it visible in Ubuntu?

Thanks,
Tom Kear

---

### Post by annda on 2007-07-31
could you post the output of the command

```
sudo fdisk -l
```

to see what partitions are recognized. the file /etc/fstab says which partitions should be mounted at boot. can you post that too?

---

### Post by dpar on 2007-07-31
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by AnotherMuggle on 2007-07-31
> **annda said:**
> could you post the output of the command

```
sudo fdisk -l
```

to see what partitions are recognized. the file /etc/fstab says which partitions should be mounted at boot. can you post that too?

```
sudo fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15200   122093968+   b  W95 FAT32

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3321    26675901    7  HPFS/NTFS
/dev/hda2            3322        6642    26675932+   7  HPFS/NTFS
/dev/hda3            6643        9703    24587482+  83  Linux
/dev/hda4            9704        9964     2096482+  82  Linux swap / Solaris


```
/etc/fstab
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=37bcdb8f-81db-4386-ab91-3602c93e23e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=1004079A63805C76 /media/Vista    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=36E9571C4741E093 /media/XP       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=e7260909-40f4-4783-bee9-8c25acb061eb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

Also, when clicking on the Windows XP partition in Computer I get this error message:
[IMG]http://img59.imageshack.us/img59/8315/screenshotgnomemountrn9.png[/IMG]

---

### Post by nofrak on 2007-07-31
Can you mount it manually?  Command would be "sudo mount /dev/hda1"

---

### Post by AnotherMuggle on 2007-07-31
> **nofrak said:**
> Can you mount it manually?  Command would be "sudo mount /dev/hda1"

tom@tom-desktop:~$ sudo mount /dev/hda1mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

---

### Post by AnotherMuggle on 2007-07-31
> **dpar said:**
> [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

I didn't ignore the link btw, I'm taking a look but this is all new to me.

---

### Post by annda on 2007-07-31
your fstab looks ok to me... can you see the xp partition with the mount command? without parameters it displays all mounted partitions. if not, can you mount it manually?

```
sudo mount -t ntfs /dev/hda1 /media/XP
```

---

### Post by Inxsible on 2007-07-31
Do you have a folder called XP under /media. You need to have the folder there already to be able to mount it.

I ask because, the error message said Cannot mount 'Windows XP' which is different from XP

I could be on a complete tangent tho

---

### Post by AnotherMuggle on 2007-07-31
> **annda said:**
> your fstab looks ok to me... can you see the xp partition with the mount command? without parameters it displays all mounted partitions. if not, can you mount it manually?

```
sudo mount -t ntfs /dev/hda1 /media/XP
```

Thanks for the help.
The command presents me with the following:
[IMG]http://img48.imageshack.us/img48/5161/screenshotnautilusse0.png[/IMG]

---

### Post by Inxsible on 2007-07-31
As an aside, your fstab lists those drives as ntfs, so you wont be able to write to those drives. You need to install ntfs-3g to be able to write to the NTFS file system.

Of course, this is a problem for later...after you have been successful in mounting the drives. :)

---

### Post by Inxsible on 2007-07-31
I guess you did mount it to XP now.

you can change ownership by 

```
sudo chown -R <your username>:<your group> <path to mount point>
```so for you ..assuming your user name to be tom

```
sudo chown -R tom:tom /media/XP
```

---

### Post by AnotherMuggle on 2007-07-31
> **Inxsible said:**
> Do you have a folder called XP under /media. You need to have the folder there already to be able to mount it.

I ask because, the error message said Cannot mount 'Windows XP' which is different from XP

I could be on a complete tangent tho

A folder called "XP" does exist in /media.  Clicking on it gives me that same permissions error message.

---

### Post by Inxsible on 2007-07-31
> **tomkear2006 said:**
> A folder called "XP" does exist in /media.  Clicking on it gives me that same permissions error message.

just change the owner of the mount point as I listed in post 12.

You should be good to go !

---

### Post by AnotherMuggle on 2007-07-31
> **Inxsible said:**
> just change the owner of the mount point as I listed in post 12.

You should be good to go !

I ran the command but the partitions no longer visible in Computer and when I run the command to mount it, it says its already mounted or busy.

tom@tom-desktop:~$ sudo mount -t ntfs /dev/hda1 /media/XP
mount: /dev/hda1 already mounted or /media/XP busy
mount: according to mtab, /dev/hda1 is already mounted on /media/XP

---

### Post by Inxsible on 2007-07-31
> **tomkear2006 said:**
> I ran the command but the partitions no longer visible in Computer and when I run the command to mount it, it says its already mounted or busy.

tom@tom-desktop:~$ sudo mount -t ntfs /dev/hda1 /media/XP
mount: /dev/hda1 already mounted or /media/XP busy
mount: according to mtab, /dev/hda1 is already mounted on /media/XP

What do you mean not visible in Computer? Did you try browsing to the location using nautilus or the terminal ?

---

### Post by AnotherMuggle on 2007-07-31
> **Inxsible said:**
> What do you mean not visible in Computer? Did you try browsing to the location using nautilus or the terminal ?

Through the GUI.

---

### Post by Inxsible on 2007-07-31
> **tomkear2006 said:**
> Through the GUI.

and you are saying that the folder didnt exist there?

Go to Places -- > Computer --> media and see if the folder XP is still there

---

### Post by AnotherMuggle on 2007-07-31
> **Inxsible said:**
> and you are saying that the folder didnt exist there?

Go to Places -- > Computer --> media and see if the folder XP is still there

The directory is still there.

---

### Post by Inxsible on 2007-07-31
> **tomkear2006 said:**
> The directory is still there.

so whats the problem then?

you said that it was not visible, correct?

I am sorry, maybe I am mis-understanding you or something

---

### Post by aysiu on 2007-07-31
Ubuntu-Geek has [a wonderful tutorial on this](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html), complete with screenshots.

All of this, including selection of the mount point and enabling of read/write on NTFS, can be done through pointing and clicking:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by AnotherMuggle on 2007-07-31
> **Inxsible said:**
> so whats the problem then?

you said that it was not visible, correct?

I am sorry, maybe I am mis-understanding you or something

If I go to Places -> Computer, I see a list of all the partitions.  The Windows XP one has gone.

---

### Post by shagster_ on 2007-07-31
```
sudo chmod 777 /media/XP
```

---

### Post by aysiu on 2007-07-31
> **shagster_ said:**
> ```
sudo chmod 777 /media/XP
```
Uh, you can't *chmod* an NTFS drive.

---

### Post by AnotherMuggle on 2007-07-31
> **aysiu said:**
> Ubuntu-Geek has [a wonderful tutorial on this](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html), complete with screenshots.

All of this, including selection of the mount point and enabling of read/write on NTFS, can be done through pointing and clicking:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Followed this guide and got the mount working, though its still not writeable.  Not important though :-)

EDIT: After a restart the drives are mounted and accessible - RW.
Thanks for everyones input.

---

### Post by jhpope on 2007-07-31
i get the cannot contain the following characters when i try to use ntfs configuration tools...any ideas?

EDIT:
nevermind...the ntfs config tool works great! you just need enter what you want the drive to be called and not a path. also you do not and shouldn't create that path as it will tell you it is already in use if you try to

---

