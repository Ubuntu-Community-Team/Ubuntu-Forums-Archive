---
title: "[SOLVED] Can't mount or write to external HD"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by ninja_in_pajamas on 2007-09-26
I'm trying to mount a 320 gig FreeAgent external hard drive.  I got it to mount a little while ago using the command  sudo mount /dev/sdb1 /media/external -t ntfs -o umask=0002,nls=utf8

It mounted once but I could not write to it.  ntfs-3g was installed prior to doing this.

Tried to remount it a little while ago and it cannot find it at all now.

I have posted the dmesg log for it at [http://paste.ubuntu-nl.org/38737/](http://paste.ubuntu-nl.org/38737/)

Any ideas on what I can do to remedy this?  I also tried to do an ntfsfix on it but ntfsfix couldn't see it either.

---

### Post by eph1973 on 2007-09-26
Sounds like you already had it formatted to NTFS, like you were maybe using it for Windows XP before.  Is this the case (i.e. it's not a new external HD, right?).

---

### Post by ninja_in_pajamas on 2007-09-26
It is a brand new drive actually.  It is pre-formatted in ntfs, and I have a dualboot setup.  I would really prefer to be able to use it on both XP and Ubuntu because Ubuntu doesn't play back dvd rips very well with an ATI card.  Also, I need to read it because I have another external full of files I would like to be able to access in Ubuntu.

---

### Post by eph1973 on 2007-09-26
I would try using a formatting/partitioning utility (such as GParted), and make a partition in FAT32 (big enough to hold the files you wish to share, and maybe a ext3 partition (for linux only).  Or you could just do the whole thing in FAT32, whatever you wanted, and make the mount point something like /windows or something to that effect.  If you don't have GParted installed, just type
```
sudo apt-get install gparted
```in your terminal.
Then go to System>Administration>GNOME Partition Editor to start it.

---

### Post by ninja_in_pajamas on 2007-09-26
Ah, and therein lies the problem.  I can't use fat32 because I have numerous files that are well above 4 gigabytes.

---

### Post by eph1973 on 2007-09-26
Have you tried to use GParted and reformat it using the NTFS selection there?  I am not sure that would work, but I've always reformatted HD's after I bought them, even if they were pre-formatted.  I have a FreeAgentDesktop 500MB and have no issues, although I don't run an NTFS on it.  Because you specifically want to run NTFS, anything else I would have to say at this point would be basically an educated guess.  I have to go somewhere at the moment, and if no one with more knowledge has posted a good reply, when I get back, I can help search for web pages that might help you.  Good luck.

---

### Post by ninja_in_pajamas on 2007-09-26
Okay.  Took care of the mounting issues.  I can mount it with no problems.  I STILL cannot write to it though.

---

### Post by qpieus on 2007-09-26
What are the permissions on /media/external ?```
ls -la /media
```
to find the permissions and owner of the /media/external directory. Maybe you don't own it or have permission to write to that directory.

---

### Post by eph1973 on 2007-09-27
You might want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=217009").  Of particular interest to you (since you already have the 3g program) you might want to see how he suggested to configure it.  I hope that helps a bit.

---

### Post by ninja_in_pajamas on 2007-09-27
I know for sure that permissions is part of the issue.   After doing some tinkering, I've noticed that the problem it multi-tiered.  Along with the permissions issue, there is also an issue with unmounting the drive. Ubuntu says it can't find some file. Because of that I have to manually mount the drive every time and the drive is assigned a different identifier every time (sdb,sdc,sdd,sde...etc.).  Due to how much crud I'd have to go through to fix all of those problems, I'm going to just format the drive in Fat 32, compress what videos I can (anyone know a good FREE dvd to avi conversion program?) and hope I don't have any problems trying to do things that way.

Thanks for the help eph1973 and qpieus.

---

