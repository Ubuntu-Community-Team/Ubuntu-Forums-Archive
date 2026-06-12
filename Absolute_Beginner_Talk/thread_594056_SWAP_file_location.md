---
title: "SWAP file location"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Disker on 2007-10-27
One more time...

WHen I loaded Gutsy I created two partitions prior to the install.  The first for the OS and a second swap partition of 2Gig to use as the swap file space.  How can I tell if it being utilized as planned or if the OS is using part of the OS partition as swap space?  

Once I find it and if it's not correct can I reassign the swap to the 2Gig partition?

Thanks

---

### Post by Pumalite on 2007-10-27
You can check if your /swap partition is being mounted in /etc/fstab

---

### Post by dfreer on 2007-10-27
You can also see how much swap your system is using by checking your system monitor. In gnome, System > Administration > System Monitor.
I don't think ubuntu will just use part of the OS partition as swap space, you'd have to set it up to do that.

---

### Post by Disker on 2007-10-27
I looked in etc but there is no fstab there.   Not a good start I would say.

---

### Post by justsomedude on 2007-10-27
You can open fstab by typing

```
gedit /etc/fstab
```

in a terminal :)

---

### Post by Disker on 2007-10-27
Got it and see a problem already but not sure what to do about it.  Here's a paste from the screen.  The sda6 is the swap partition I created.  

So no I have to fix this and then get Gutsy to use it...right?

Thanks


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=4e4cdd74-5c77-4abc-9406-9eb96a4aac29 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2F0E-140F  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=8C18-9766  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=feb12213-ac7a-40af-930c-bb10d60ce6a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Can+~ on 2007-10-27
I was just curious with this post, and checked** my fstab**:

> # /dev/sda6
UUID=7a261f7a-d994-4f78-ab32-393627802e18 none            swap    sw              0       0

"none". Meanwhile all other partitions are mounted on "/media/...". And... I guess this is not good, where should I mount it?

---

### Post by Old Pink on 2007-10-27
Install "gparted" from the repositories, then go System > Administration > GNOME Partition Editor

You'll then have the tool you used to create the partitions. And you can check how everything has been set up.

---

### Post by Pumalite on 2007-10-27
Post:
blkid

---

### Post by Pumalite on 2007-10-27
This is mine:

# /dev/sdc5
UUID=323db2cb-950e-4ab2-bcfe-5e72724b826c none            swap    sw              0       0

So, replace things accordingly and you'll be fine.

---

### Post by Can+~ on 2007-10-27
Resource managare uses 0 / 1.9 GiB. So mine it's working. Good to know.

---

### Post by dfreer on 2007-10-27
> **Disker said:**
> The sda6 is the swap partition I created.  

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=4e4cdd74-5c77-4abc-9406-9eb96a4aac29 **/   ext2**    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2F0E-140F  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=8C18-9766  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=feb12213-ac7a-40af-930c-bb10d60ce6a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

> **Pumalite said:**
> This is mine:

# /dev/sdc5
UUID=323db2cb-950e-4ab2-bcfe-5e72724b826c none            swap    sw              0       0

So, replace things accordingly and you'll be fine.


**DON'T** mess with that /dev/sda6, I don't know how your install got messed up, but it's definitely not your swap partition (**/dev/sda7** is). Your root filesystem is currently mounted on /dev/sda6, so don't mess with it. /dev/sda7 looks like it is currently used as swap, so your fine.

> **Can+~ said:**
> I was just curious with this post, and checked** my fstab**:

"none". Meanwhile all other partitions are mounted on "/media/...". And... I guess this is not good, where should I mount it?

That line is fine, swap doesn't get mounted like normal filesystems, considering it isn't really a filesystem anyways.

---

