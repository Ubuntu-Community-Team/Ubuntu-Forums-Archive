---
title: "Hello - first post first question..."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Z1QR20 on 2007-06-01
Hi.


Just installed Ubuntu after my XP drive tanked. I used Mandrake 9 some years ago and enjoyed it but could not get the family to get on board. I think Ubuntu might do the trick. I like it.


One question - 

Is there a good, easy file recovery program that can run in Ubuntu to recover my files off the XP drive? I installed Ubuntu on a different drive and when I boot into it with the old drive installed as a slave it can see that there is a drive there but it can't mount it. The XP file system is toasted but I know the files are there - I was able to see them with a demo program under XP on yet another drive. The full version is like $69 and I don't want to spend another dime on a Windows app if I am going to be abandoning it.

So in short - with Ubuntu running is there a cool app i can use to get the files back?

---

### Post by starcraft.man on 2007-06-01
Well, if you ask me what I recommend most for working (almost) 100% of the time, that would be [spinrite]("http://www.grc.com/spinrite.htm") (god I love it, saved me twice on my old comp). There are of course ways of getting it for free if budget is the problem (it regularly costs almost 90, well spent dollars). *coughs* [Torrent...]("http://isohunt.com/") 

As for runner up, I've heard good things about [testdisk.]("http://linuxappfinder.com/package/testdisk") I haven't personally used it though... pick one and see how it works :).

Data recovery is a pain....

---

### Post by chamberlain2006 on 2007-06-01
If you just need to get some files off your NTFS (windows) formatted drives, install ntfs-config (it will install dependencies).  Then go to System>Administration>NTFS Drives (or something like that) to configure it.

---

### Post by starcraft.man on 2007-06-01
> **chamberlain2006 said:**
> If you just need to get some files off your NTFS (windows) formatted drives, install ntfs-config (it will install dependencies).  Then go to System>Administration>NTFS Drives (or something like that) to configure it.

Uh... the drivers are only for writing.... Ubuntu can still mount, read and copy off of NTFS no (i've done so)?

I assume he has data corruption if it fails to mount.

---

### Post by tyler_roach on 2007-06-01
As long as your files are still intact, it should be very easy to retrieve them; all you have to do is mount your windows xp partition. There are two ways of doing this --

One is to install automatix ( [http://www.getautomatix.com](http://www.getautomatix.com)). From it you can install a utility that automatically mounts your FAT and NTFS partitions.

The other is to follow the instructions here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If neither of those work, it would indicate that your file system is corrupt.  However, you should be able to restore it by using the fsck or the testdisk utility. I'd be glad to help you with that if you need assistance.

---

### Post by Z1QR20 on 2007-06-01
> **starcraft.man said:**
> 
I assume he has data corruption if it fails to mount.
Exactly. It won't boot into XP off that drive and the drive is not accessable in XP when I install the drive as a slave.

I can get to the files with a couple different file recovery apps in XP (PC Inspector and a couple others)
, so I know they are there.

---

### Post by Z1QR20 on 2007-06-01
> **tyler_roach said:**
> 

If neither of those work, it would indicate that your file system is corrupt.  However, you should be able to restore it by using the fsck or the testdisk utility. I'd be glad to help you with that if you need assistance.

This would be the case. The partition info is toasted, hence there is no partition to mount.

I will look into testdisk when I get home (On my work XP laptop right now)

---

### Post by Z1QR20 on 2007-06-02
Two words:

File Scavenger.


Ran it in XP, got all of my files back with the original file names and directories. Backed up onto an external drive, and I'm double archiving everything onto DVD's today.


Now to pull everything into Ubuntu and I'm all set.

---

