---
title: "how do I mount a FAT32 drive?"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by reynoldlariza on 2005-05-31
how do I mount my drive C:\ and D:\ to be accessible to ubuntu?

I like to share files between Ubuntu and WinXP.

sorry, im kind'a noob ;-)

---

### Post by sethmahoney on 2005-05-31
First you have to figure out which partition is the FAT32 partition.  If its on your first hard disk, it will be /dev/hda with a number after it, if its on your second hard disk it will be /dev/hdb with a number after it, and so on.  The number tells you which partition on the disk it is.  If you had Windows running before linux, it will likely (I think - I might be wrong) be /dev/hda1 .  Once you figure it out, type at the terminal:

cd /
sudo mkdir winmount
sudo mount -t fat32 /dev/hda# /winmount       (replace # with the correct number)

And then all the files on your fat32 drive will show up in /winmount until you reboot.  Making it more permanant is more tricky, but if all you want to do is copy stuff over a linux partition, that should get you started.  If you want to have a permanantly accessable fat32 partition, let us know and we'll show you how to do it.

Hope that makes sense!

---

### Post by Chibi Mei on 2005-06-24
Hi, I just tried the above to mount a newly formatted and partiononed fat32 (200gb HDD). But "sudo mount -t fat32 /dev/hdb1 /fat32" gave "mount: unknown filesystem type 'fat32'". So I tried with vfat instead of fat32 and it said: 
```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
The drive is the second drive (D:) so hdb1 should be correct, right?

Thanks in advance!
 -Vicky

---

### Post by POET250 on 2005-06-24
according to seth it would be hdb1

---

### Post by bogdan85 on 2005-06-24
hy
I´ve just tried this and it worked. I mounted a NTFS partition, named hdb1. I just have a silly little question. When logged as root I can see the files in this partition using the dir command. How can I see them in Nautilus?  ](*,)

---

### Post by Chibi Mei on 2005-06-24
Ah, nevermind. It was hdb1, it was just that the partioning and formatting had failed somehow, so I redid it on another computer then attached the HDD again, and hdb1 worked just fine. :] The only difficulty I'm facing now is that I can read files from it but not write, and I've tried chown as well as chmod with sudo, but it still won't change anything.. anyone know why? :) 

Thanks in advance, 
Vicky

---

### Post by Wolki on 2005-06-24
You can see what partitions you have with

```
sudo fdisk -l /dev/hd?
```

If you have multiple partitions the numbering can be a little confusing. It will tell you which partitions are from Windows, so just try to mount these.

> Ah, nevermind. It was hdb1, it was just that the partioning and formatting had failed somehow, so I redid it on another computer then attached the HDD again, and hdb1 worked just fine. :] The only difficulty I'm facing now is that I can read files from it but not write, and I've tried chown as well as chmod with sudo, but it still won't change anything.. anyone know why? 

Try 

```
mount -t vfat -o rw /dev/hdb1 /fat32
```

if that doesn't work you have to mount it wth you user id:

```
mount -t vfat -o rw,uid=<your user id> /dev/hdb1 /fat32
```

you can find out you user id in the gnome user manager, remove the <>s :)
hope this helps, it#s been a long time since i had to mount fat drives ^^;;

---

### Post by carlc on 2005-06-24
You might as well set it to mount when your system boots. Have you check the [Ubuntu Guide](http://www.ubuntuguide.org/#automountfat)?

---

