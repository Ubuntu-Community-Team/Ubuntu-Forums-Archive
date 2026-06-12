---
title: "Can't edit drive with my files on it... :("
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by SuperGrouper on 2008-01-10
I have a Sony Vaio with an (approximately) 200 gigabyte hard drive, which came installed with Windows Vista, which is every bit as terrible as people say.  I left Vista installed as a dual-boot due to some issues that Linux cannot yet fulfill.  Anyway, I shrank the drive and partitioned it into several sub-drives so that I could install Linux and one of those drives is a 100 gigabyte FAT-32 drive.  I made it to hold my files in because both OS can read fat32.  I made it on an extended partition because between Vista and Linux's requirements there were too many for them to all be primary.

I am running the latest version of Kubuntu, which I decided to try after Ubuntu crashed (my fault.)  It works well for my specific needs...  Anyway, the problem is that Kubuntu won't let me edit the files there, or even use them!  I have all of my music there and I have installed the necessary codecs to play it- but the Amarok tries to play it and produces no noise while Listen can't even load the mp3s.

When I was logged into Vista I changed the partition's name to "files."  Could that have screwed up the permissions somehow?  I don't know if this problem existed before, since I hadn't tried playing the music until now.

I've tried running konqueror and dolphin as root to change the permissions for /media/sda7, but it doesn't seem to be working...  Frustrations like this almost make me want to quit Linux...  The over-controlling OS and compatibility issues are the reason I hate Vista, and it's starting to seem like Linux has some of the same issues, but I refuse to give up...  I'm still new to this.  Could someone please help me?

---

### Post by webofunni on 2008-01-10
Just try this 

Press Ctrl + Alt + F1 and login as root .. 
enter command startx -- :2 

it will log you in to root gui ... try from there

---

### Post by kwacka on 2008-01-10
Can you post your fstab file?

---

### Post by OffAxis on 2008-01-10
> I made it to hold my files in because both OS can read fat32
true, but you may not know that a generic install of ubuntu's latest (7.10) can now read and write to ntfs.

So what are the permissions on the files?
navigate to the folder and
```
ls -l
```

---

### Post by SuperGrouper on 2008-01-13
> **OffAxis said:**
> true, but you may not know that a generic install of ubuntu's latest (7.10) can now read and write to ntfs.

So what are the permissions on the files?
navigate to the folder and
```
ls -l
```

The permissions are these-

-rwxrwx---   1 root plugdev 9297463 2007-06-01 18:21 01-Dancing Queen.mp3
-rwxrwx---   1 root plugdev  801672 2008-01-08 12:18 2080108snowfoxwall.png
drwxrwx---   6 root plugdev   65536 2008-01-04 17:56 downloads
drwxrwx---   2 root plugdev   65536 2008-01-10 14:54 files
drwxrwx--- 183 root plugdev   65536 2008-01-07 14:32 music files
drwxrwx---   3 root plugdev   65536 2008-01-04 17:56 $recycle.bin
drwxrwx---   5 root plugdev   65536 2007-12-29 19:24 SWGallery_old
drwxrwx---   2 root plugdev   65536 2008-01-07 10:17 Temp
drwxrwx---  14 root plugdev   65536 2008-01-06 18:11 wip

Ironically, it will let me copy and paste files- the Dancing Queen mp3 file is from one of my Dad's CDs that I dumped in music files.  I wanted to see if I could copy and paste and the system let me do that, at least...

I tried logging in as root using the terminal but the graphical interface wouldn't start when I entered startx --:2.  It said something about a problem with a server...

---

