---
title: "how do i mount my linux partition"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2008-02-24
any idea? i have a internal drive.

---

### Post by Crafty Kisses on 2008-02-24
First you have to determine what the partition is called and what filesystem it is. One quick way to do it if you know what filesystem you formatted the drive as (Ext3, for example) is to just type the terminal command:

```
sudo fdisk -l
```

It should turn out something like this:

```
Disk /dev/hda: 20.0 GB, 20020396544 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes 

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1275 10241406 83 Linux
/dev/hda2 1276 2434 9309667+ 5 Extended
/dev/hda5 1276 2388 8940141 83 Linux
/dev/hda6 2389 2434 369463+ 82 Linux swap / Solaris
```

Then you would create a mount point by doing the following:
```
sudo mkdir /storage
```

Alright, hope this helps.

---

### Post by angrboda on 2008-02-24
Hi,
I take it we are talking about an extra partition? And you want to be able to mount it as a normal user, preferably by clicking on its icon in Nautilus? What filesystem does it use? 
Assuming it is formatted with the (default) ext3:

1) Follow Codename's advice and find out which device it is (if you do not know)
2) Create a mount point as Codename described
3a) (the ubuntu way ;) )  Find out the uuid of the partition in question:

```
blkid /dev/hdax
```

(replace "hdax" with your actual device, of course)

4a) Edit /etc/fstab via

```
sudo vim /etc/fstab

```
(replace "vim" with your favourite editor)
and add somthing like this:

```
#/dev/hda2
UUID=3b539676-37a1-4122-82f0-db75dde4f839 /storage ext3 defaults,user,rw,noauto  0 1

```
where the number is of course the uuid you get in step 3a

alternatively:

forget 3a) and
3) add the following to your fstab:
```
#/dev/hdax
/dev/hdax /storage ext3 defaults,user,rw,noauto  0 1

```

where, again hdax is replaced by the device in question.

I recommend doing this the standard "ubuntu way" through 3a) 4a).

If the filesystem is not ext3 replace the "ext3" entry in the fstab line with the fs you are using.

Good luck and happy linuxing

---

