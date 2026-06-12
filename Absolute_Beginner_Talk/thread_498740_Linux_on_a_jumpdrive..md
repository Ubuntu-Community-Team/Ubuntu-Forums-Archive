---
title: "Linux on a jumpdrive."
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-07-11
My buddy's MAC OSX took a dive on him, yet somehow he knows his files are still there. Can he put Linux on a jumpdrive, boot to it, and somehow retrieve his files? 

Would Ubuntu be a good candidate for this or should you use something like DamnSmallLinux?

---

### Post by scxtt on 2007-07-11
doesn't he have a cdrom?  i'd save space (i.e. no OS) on the jumpdrive and put files on it after booting a LiveCD ...

---

### Post by solar george on 2007-07-11
I would use a livecd - you could try ubuntu and copy the files to a usb disk.

---

### Post by Roasted on 2007-07-11
So using a LiveCD he can access the files and copy them over? It would mount the partition where his stuff is in the OSX side?

---

### Post by Atomic Dog on 2007-07-11
> **Roasted said:**
> So using a LiveCD he can access the files and copy them over? It would mount the partition where his stuff is in the OSX side?

I would think you could mount it.

---

### Post by Roasted on 2007-07-12
How would you do that? I can't see anything in the wiki about MAC OSX mounting.

---

### Post by Topfs on 2007-07-12
If you use the latest release, Fiesty Fawn. 7.04 I'd think you just go to Computer and double click the partition and it should automount. It does this atleast on my ntfs and similair but I can't answer for sure with the MacOSX filesystem but I think it should based that they use EXT3 or ReiserF or their own thingy but I think all are reminense from the *nix and bsd world. Not sure though. But worth the try :)

Oh check the computers CPU before downloading the ISO, PowerPC for the old, nonintel mac and x86 for the newer if I have my facts right.

God luck.

---

### Post by ghost_ryder35 on 2007-07-12
your not mounting OSX your mounting the partition.  It's just the same as you can mount windows partitions and write to them even though they are not linux (unless there NTFS then you can only read, unless using an unrealable write tool).  However OSX was built around FreeBSD which is based on unix which Linux is also based on so the probability of you being able to read it is practically 100% (might run into issues if it is encrypted, or running something similiar to NTFS with lots of file system rules), but you got nothing to loose booting the live CD and trying to mount it.  I am pretty sure it will be a success!

---

### Post by osx424242 on 2007-07-12
It can probably be done.  I never got around to it during the weekend I played around with Ubuntu, but found plenty of threads on this forum that discussed it.  Because OS X uses a Journaling file system, unless your friend turned it off you might have some issues.

Try [http://ubuntuforums.org/showthread.php?t=311476](http://ubuntuforums.org/showthread.php?t=311476)  (if the URL gets pulled, it's thread 311476 on ubuntuforums) for one example of how people here tried to access OS X files from Ubuntu.

Or do a Google search for "journaling os x site:ubuntuforums.org" (the above link was the 2nd result).

Did your friend try booting using the OS X Install CD?

---

### Post by C.S.Cameron on 2007-07-12
I am writing from Ubuntu running off an 8GB USB stick. I also have it running on a 4GB, but after installing Wine, Acad2000 and Rhino 3D there is not much room left.
Installing on a jump drive  you can install other applications that might help.
Use a fast Jumpdrive or SD card, 30MB/s should work as good as a ATA drive.
The question is if his Mac BIOS can boot from USB.
Cork

---

