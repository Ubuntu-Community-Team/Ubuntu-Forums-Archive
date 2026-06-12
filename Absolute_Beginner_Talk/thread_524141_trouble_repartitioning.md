---
title: "trouble repartitioning"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by holdie on 2007-08-12
I just got a 500GB mybook, and I've decided to repartition my laptop harddrive (which is currently about 60 gigs windows, 20 gigs linux) to only about 15 for a barebones windows (with photoshop unntil I can finally let go)

problem is, I've whittled down my window partition, but gparted doesn't give me the option to repartition as it did when I first installed linux.  There is a warning flag on my sda2 (windows) partition saying that it "can't find the mount point" even though i have full ntfs-3g access to it and can read/write from my linux OS...any ideas as to what I should do here?

thanks

---

### Post by bren on 2007-08-12
partition ops sometimes run better when you boot from the LIVE CD.   try that
if no luck post back

bren

(sometimes windows partition not visible because not mounted or because partition table messed up.  in latter case use utility testdisk to repair)

---

### Post by holdie on 2007-08-15
I downloaded the Live CD and it is not recognizing my windows partition, however when I try to resize it two things happen

1. I can't resize the NTFS partition because it says it is read/write mounted...but when I unmount it, it automatically mounts again...

2. I can't expand my current ext3 linux partition to take up the free space left over...I don't know why, but it won't allow me to expand it, though perhaps this is because the NTFS isn't actually shrunk yet, only theoretically so

any ideas?

---

### Post by amazingtaters on 2007-08-15
Holdie, I'm gonna link you here, because I just did this. I had a heck of a time getting it to work. Read through the thread, see what you can get out of it. I make no promises, as I'm still a bit confused. Or, more than a bit. Anyway, read away.

[http://ubuntuforums.org/showthread.php?t=524980](http://ubuntuforums.org/showthread.php?t=524980)

That's about all the help I can think of at the moment, but don't be afraid to ask for more.

---

### Post by Arthur Archnix on 2007-08-15
Well, I'm not too sure about XP, but Vista has the ability to reduce it's size by half. You have to reduce by half and then expand your Linux partition. Then reboot into Windows Vista to reduce it further (if you skip the booting into Linux and taking up the space you freed Vista will take over the free space again. At least, that's what happened to me!)

You also have to be sure to defrag your windows hard drive before each resize. 

If it's not Vista, I'd download a gparted live cd. Boot into windows, defrag. Boot the Gparted CD and resize by about 60%. If that doesn't make your Windows drive small enough, then defrag and repeat, but be sure to never shrink less than 60% or windows +1Gig to be safe. Otherwise you risk messing up your windows install.

Many people - including me - recommend backing up your important information before doing any repartitioning, because strange things do happen, unlikely as that may be.

If it's not Vista or XP I can't really say much from experience. Windows 2000 should be ok to proceed like XP, but anything prior to that I'd be inclined to wipe the hard drive, create my partitions with a gparted live cd prior to installing, then install windows, then ubuntu.

---

### Post by amazingtaters on 2007-08-15
That's a great idea there. I had forgotten GParted came on a live cd, even though now that it was mentioned I remember debating wether to burn one last night. Maybe I still should.

---

### Post by holdie on 2007-08-15
Yeah, I actually am already using Gparted on a Live CD...when I tried it from my Ubuntu desktop it wouldn't recognize the mount point of my NTFS partition...I'm going to give the defrag a shot and see how that helps me, and thanks for the advice on the no more than 60% at a time thing, I was originally going from 70GB to 15GB so that may have messed something up...I'll try this out and get back to you guys

---

### Post by holdie on 2007-08-15
I've gotten LiveCD to reduce the size of the NTFS partition (did it twice, both by about 60%), but now I can't expand my ext3 (linux) partition to engulf the freed space...my hard drive looks like one 20 GB NTFS partition, then a 40 gig free space area, then my ext3 which is made up of both the swap and my linux partition...

When I choose to resize ext3, it won't let me move the arrow to the left...any ideas?

---

### Post by jw5801 on 2007-08-15
Are you using the version of GParted on the Ubuntu or the GParted LiveCD (see my signature for links)? The version on the Ubuntu CD is the same as the one in the repos and is a very old version. It doesn't allow for moving an ext3 partition to the left. The GParted LiveCD however is a much newer version of the software and will let you do this.

---

