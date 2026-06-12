---
title: "creating ram disks (im confused)"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by u-slayer on 2007-08-11
So I wanted to create a ramdisk for temporary storage of files that I don't want written to the hard disk.

I did this through the command

sudo mount -t ramfs none /mnt/ram

This appears to work. However I have a couple problems. Apparently nautilus can't work with this because ram space is allocated on the fly. So I tried creating a file using the command line to test this thing out.

sudo dd if=/dev/sda of=/mnt/ram/sda.img bs=1024 count=100000

this successfully copies the first 100 megs of my hard drive to a file. However when I was watching the ram usage it doesn't appear to spike. So if this file isn't stored in ram, then where is it stored? The file does exist somewhere, I can read it with ghex2 (which does cause ram usage to spike) Can someone please explain what is going on?:confused:

---

### Post by asmoore82 on 2007-08-11
you have stubmled on to some of Linux's Magnificent RAM handling methinks.

if you don't want temporary files written to the hard drive, add this line to the bottom of your /etc/fstab file ...

```
tmpfs           /tmp            tmpfs   defaults        0       0
```

and after your next boot, the system wide temp folder /tmp will be a RAMdisk.
'tmpfs' is a highly advanced RAMdisk filesystem that has completely replaced the other in most cases

---

### Post by kerry_s on 2007-08-11
your doing it wrong.

i've used this guide, changed for my needs, but it should help you to understand how it works.
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

i think in ubuntu you need to use rd1, not rd0, ubuntu uses rd0 to load the image. make sure you check which 1 it's using or you'll get a long start or freeze.

---

### Post by u-slayer on 2007-08-11
> i think in ubuntu you need to use rd1, not rd0, ubuntu uses rd0 to load the image. make sure you check which 1 it's using or you'll get a long start or freeze.

I don't think that is going to be a problem. I'm doing this all with a bootup script that is launched from /etc/rc.local Ubuntu should be long done with ram0 by now.

> you have stubmled on to some of Linux's Magnificent RAM handling methinks.

if you don't want temporary files written to the hard drive, add this line to the bottom of your /etc/fstab file ...

Is it Magnificent because it is using the ram without reporting it in the system monitor? I can't thnk of any other way it could be doing this since I have no swap partition.

---

### Post by bogolisk on 2007-08-11
> **u-slayer said:**
> So I wanted to create a ramdisk for temporary storage of files that I don't want written to the hard disk.

I did this through the command

sudo mount -t ramfs none /mnt/ram

This appears to work. However I have a couple problems. Apparently nautilus can't work with this because ram space is allocated on the fly. So I tried creating a file using the command line to test this thing out.

sudo dd if=/dev/sda of=/mnt/ram/sda.img bs=1024 count=100000

this successfully copies the first 100 megs of my hard drive to a file. However when I was watching the ram usage it doesn't appear to spike. So if this file isn't stored in ram, then where is it stored? The file does exist somewhere, I can read it with ghex2 (which does cause ram usage to spike) Can someone please explain what is going on?:confused:

ramfs/tmpfs use ram from the pagecache. Depends on your system, 100M might or might not show any spike in the unified pagecache. On my machine, the pagecache is currently sitting at 1.3Gig so 100M is kinda small.

Btw, you likely want to use tmpfs and not ramfs.

In linux, you always read/write to the pagecache even if you think you're read/write from/to disk (except for direct-i/o). So the pagecache is where everything happens while the disk is just backing store. tmpfs/ramfs is a filesystem without backing store. So from the user POV, it's not very different from normal files (with backing store).

---

### Post by Rob_H on 2007-12-14
Hi all. I needed a ram disk and stumbled on this thread. Thanks for the pointer regarding tmpfs. I'd been fiddling with ramfs for a while, and another disadvantage of it seems to be that there's no way to set default permissions on the root directory. So every time I mounted it, only the root user could write to it. But tmpfs works great, and the memory it uses does show up in monitoring tools (e.g. KSysGuard).

---

