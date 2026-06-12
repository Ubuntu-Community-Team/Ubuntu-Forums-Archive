---
title: "Accessing Second Partition..."
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by james.gornall on 2006-10-17
I've just created a partition on my hard drive.

I kno this might sound really stupid, but how do I access it in Ubuntu?

I'm totally noob I know but hey gotta learn sometime.

Thanks.

---

### Post by bulldog on 2006-10-17
Well if you know what the linux name is of your new partition............

Mounting can be done on different ways.
I give you one.
```
sudo mkdir /mnt/folder
```
```
sudo mount /dev/??? /mnt/folder
```

You have to fill the ??? with the name of you partition.

If you can give me the output of,```
sudo fdisk -l
```l as in like

---

### Post by CeeDub on 2006-10-17
I have the same question. Here's my fdisk -l:
>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4524    36338998+   7  HPFS/NTFS
/dev/hda2            7298        9626    18707692+  83  Linux
/dev/hda3            9627        9729      827347+   5  Extended
/dev/hda4            4525        7297    22274122+  83  Linux
/dev/hda5            9627        9729      827316   82  Linux swap / Solaris


Don't I need to put it in fstab to make it accessible on boot? How do I do it?

---

### Post by bulldog on 2006-10-17
You can put it in fstab if you want.

You have to make a rule like this one.```
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

---

### Post by CeeDub on 2006-10-17
I need to put in the hda4 partition - the linux one.  What do I put in for the options, dump and pass?

---

### Post by bulldog on 2006-10-17
Well I suppose something like this```
/dev/hda4       /media/hda4           ext3    defaults        0       2
```

But it's possible you have to set the read and write rights correct.

---

### Post by CeeDub on 2006-10-17
Thanks for your help, it's coming along.  Now I just need to set the permissions.  I tried this:

> /dev/hda4       /media/Media    ext3    defaults,umask=007        0       2


but it gives me an error saying:
> mount: wrong fs type, bad option, bad superblock on /dev/hda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I'm not really sure what that error is even saying.  Sorry I'm such a newb

PS. The directory /media/Media does exist.  I can mount it without setting the permissions, but I can write anything to it without being root.

---

### Post by bulldog on 2006-10-17
Well I'm no expert either with this,but I can tell you that /media/Media won't work.

You mount at the /media folder and next should be the device hda4

Edit:
I suppose the name of your drive is Media in windows.
This will be detected and you should see your windows name in /media

---

### Post by james.gornall on 2006-10-17
Thanks alot for the reply.

Give it a go when I get home :)

---

### Post by CatKiller on 2006-10-17
/media/Media is fine, as long as it exists. A mount point is just a directory, and it makes sense to call that directory something that means something.

Personally I suspect either the partition is not ext3, or that setting a umask value isn't appropriate for an ext3 filesystem with its own file permissions.

---

### Post by bulldog on 2006-10-17
> **CatKiller said:**
> /media/Media is fine, as long as it exists. A mount point is just a directory, and it makes sense to call that directory something that means something.

Personally I suspect either the partition is not ext3, or that setting a umask value isn't appropriate for an ext3 filesystem with its own file permissions.

Totally agree with you,but I have no clue about rights and permissions and copied a line out of my fstab as an example.

---

### Post by james.gornall on 2006-10-17
hmm, I done the thing you asked.

```
gornall@gornall-desktop:~$ sudo fdisk -l

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1530    12289693+  83  Linux
/dev/hdb2            1531        1606      610470   82  Linux swap / Solaris
/dev/hdb3            1607       11167    76798732+   7  HPFS/NTFS

```

---

