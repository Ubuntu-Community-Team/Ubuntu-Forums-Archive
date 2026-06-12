---
title: "Munged Dual Boot"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by shams on 2007-01-02
Native OS is XP on an HP Pavillion dv1000 SE laptop.  I installed Ubuntu 6.10, but didn't like the partition setup (I had the installer do it for me).  So, I erased the extended partition-- at least, I thought I did.  

Let's cut to the chase, now gparted says my partitions look like this:

/dev/hda1          NTFS          24.5 GB
unallocated                          48.38 GB
/dev/hda4           extended     1.42 GB
    dev/hda5         linux-swap   1.42 GB
/dev/hda2            unknown       203 MB

issues:
1.)  can't boot to Windows; grub is throwing "Error 22".
2.)  can't figure out how to assign partition space from within gparted (using the Live CD)


I would like to allocate the 50 GB remaining, along the lines of 25 GB in FAT32 and the rest for /, home, and swap.  

Any help is appreciated.  :)

---

### Post by bulldog on 2007-01-02
Use the gparted live cd it's much more easy to use.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by shams on 2007-01-02
bulldog, thanks--

I booted to the gparted live cd.  

1.) it won't let me delete the linux partitions?
2.) also won't let me create an extended drive.  

/dev/hda1 NTFS 24.5 GB
**unallocated 48.38 GB**
/dev/hda4 extended 1.42 GB
dev/hda5 linux-swap 1.42 GB
/dev/hda2 unknown 203 MB

This is my partition table; I allocated about half of the bolded space above to a FAT32 drive, but then could make no more partitions.  

Can /, home, and swap all be logical drives in one partition?

why can't I just blow away everything but /dev/hda1 and /dev/hda2 (which seems to be some sort of system partition I don't want to mess with), then start over?

ugh.  I hate being an absolute beginner.

---

