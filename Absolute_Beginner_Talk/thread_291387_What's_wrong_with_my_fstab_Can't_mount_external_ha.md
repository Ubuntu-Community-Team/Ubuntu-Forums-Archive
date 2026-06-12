---
title: "What's wrong with my fstab? Can't mount external hard drive"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Roobert on 2006-11-02
I've been fighting with my fstab for a day now - I'm just not familiar with what options are required to have my external LaCie disk be automounted when it's turned on, and allow me read-only access. 

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda7       /media/dos      vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/LaCie    auto    ro,auto,user    0       0
/dev/sda2       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Can someone suggest what changes should be made to automount with read-only access?

Thanks

---

### Post by bodhi.zazen on 2006-11-02
fstab looks good to me.

Is the problem with mounting or automounting?

What happens when you type```
mount /dev/sdb1
```In a terminal? Error message or is the device mounted ro as you wish?

---

### Post by Roobert on 2006-11-02
> **bodhi.zazen said:**
> fstab looks good to me.

Is the problem with mounting or automounting?

What happens when you type```
mount /dev/sdb1
```In a terminal? Error message or is the device mounted ro as you wish?

The problem is that it gets mounted (an icon for the LaCie disk appears on the desktop), but I can't open the link in Nautilus. I get an error window which says 

```
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "LaCie".
```

:confused:

---

### Post by bodhi.zazen on 2006-11-02
Can you post the output of:
```
ls -l /media | grep LaCie
```

---

### Post by kerry_s on 2006-11-02
What file format is it? You can try, removing the entry and install ivman.

sudo apt-get install ivman

That usually takes care of those problematic external drives for me.

---

### Post by turkenator on 2006-11-02
im not that expirienced with linux either 6 monfs and counting 
this might work lets say your disk mounts to 
/mnt/sdb1 
right?
change the acess settings so every 1 can read it

---

### Post by Roobert on 2006-11-02
> **bodhi.zazen said:**
> Can you post the output of:
```
ls -l /media | grep LaCie
```

Sure thing:

```
$ ls -l /media | grep Lacie
drwxr-xr-x 2 root root     4096 2006-11-02 13:19 Lacie
```

---

### Post by bodhi.zazen on 2006-11-02
> **turkenator said:**
> im not that expirienced with linux either 6 monfs and counting 
this might work lets say your disk mounts to 
/mnt/sdb1 
right?
change the acess settings so every 1 can read it

Nice thought, but this does not work as permissions are set at the time of the mount.

[Here](http://ubuntuforums.org/showthread.php?t=283131) is a how-to on fstab if you are interesed.

---

### Post by turkenator on 2006-11-02
ok thanks for pointing it out just trying my luck :P

---

### Post by bodhi.zazen on 2006-11-02
> **Roobert said:**
> Sure thing:

```
$ ls -l /media | grep Lacie
drwxr-xr-x 2 root root     4096 2006-11-02 13:19 Lacie
```

Your permissions, fstab, and mount look OK.

I am not sure of the problem. Is the output with the drive mounted?

If not, mount and re-post.

If so, what is the output of ```
ls /media/Lacie
```?

---

### Post by Roobert on 2006-11-02
**SOLVED:**

I added the following to my fstab entry for the external hard drive:

```
/dev/sdb1       /media/Lacie    ntfs    rw,auto,user,***[COLOR="Red"]umask=007,gid=46[/COLOR]***   0       0
```

gid46 is group plugdev; I noticed that my fat32 and ntfs partitions had that gid assigned, as well as the umask value of '007'.

Thanks for the link, bodhi.zazen, I've bookmarked it for reference!

~ Roobert.

---

