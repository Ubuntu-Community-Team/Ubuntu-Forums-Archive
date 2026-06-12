---
title: "HELP!  Ubuntu killed my HFS+ portable drive..."
date: 2011-04-11
forum: Apple Hardware Users
---

### Post by skullmunky on 2011-04-11
I have a 1TB portable drive formatted HFS+ because we also use it with Macs a lot.  After writing some files to it from Ubuntu (10.10) and unmounting, the drive is now corrupted.  OSX disk utility says it is irreparable.  Linux fsck agrees that it's corrupted, though I haven't told it to try and repair it yet for fear of damaging it more.  

I think I can pursue my usual strategy of using ddrescue and laboriously extracting what I can - but what on earth happened?!!  How could it have gotten wrecked that badly that quickly?

---

### Post by edmondt on 2011-04-11
sorry to hear about that... I've been doing some mounting read only on my OSX partition as well, matching the uid and gid.

I would notice that sometimes OSX boots into a blue screen only...

So... my advice would be to use ntfs or ext2/ext3 (setup MacFUSE) and share between the two.

---

### Post by linuxopjemac on 2011-04-11
don't mount it in Linux,  then do fsck on it. It wil repair it.\

Never unplug a mounted drive without safely unmounting it...

---

### Post by skullmunky on 2011-04-11
OSX fsck won't repair it; is linux fsck better?  

I'm using OSX Disk Utility to make a disk image first, I'm thinking it would be wise to do that instead of mucking with the actual disk.  

> Never unplug a mounted drive without safely unmounting it... 

True.  Here are some more good rules to live by that I'm learning.  

Never make a desktop notification system that allows the user to think that an unmount operation has succeeded when in fact it hasn't.  Never make a filesystem so fragile that power loss during a write operation not only leaves that file corrupted but demolishes the entire filesystem structure.  Never solve that problem by implementing journaling but then greedily keep the implementation details proprietary so no other OS's can include it in their drivers, thus making it pointless. 

Most of those can be boiled down to "Just say no to Non-Free software".  

Except for the first one, which I'm going to take over to bugs.kde.org :D

---

### Post by skullmunky on 2011-04-11
It's just not my day ... I just killed another drive!  I was able to mount the initial afflicted drive read-only in ubuntu, so thought I'd try copying what I could onto another portable drive.  Portable drive #2 is also HFS+.  About 10 minutes in lots of I/O errors appeared - for the new drive!  Now this brand-new drive is also corrupted; fsck says it has sibling errors and can't be repaired.  Two hfs+ drives dead in one day ... I must be doing something bad to them.

---

### Post by linuxopjemac on 2011-04-12
Do your stuff in Linux, really. Don't use the OSX tools...

---

### Post by skullmunky on 2011-04-12
So, everything worked out ok in the end.  Though I don't understand how.  The drive just got better after resting a while or something.  

Sequence of events:

1. drive A gets corrupted.  won't mount in OSX anymore, can't be repaired with OSX tools.
2. drive A still mounts (read only) in linux.  fsck detects errors with the extents tree but can't repair it.
3. in linux, copy files from drive A to drive B (another HFS+ drive).
4. during the copy operation, drive B spews I/O errors, cp finally aborts.  checking the copied files shows most are corrupt.
5. drive B won't mount in linux or OSX.  OSX disk utility shows no partitions on the drive.
6. reattached drive A in OSX.  fatal errors still appear, advising that the disk cannot be repaired and must be reformatted.  however, it still mounts and appears on the desktop.
7. reformatted drive B in OSX.  
8. in OSX copied 500GB+ contents of drive A to drive B.  no errors.  manually verified a random selection of a few hundred files, no problems.
9. ran DiskWarrior on drive A, fixed a few minor directory structure problems.
10. drive A now mounts cleanly and passes fsck and Disk Utility verification.  
11. celebration and ritual thanks to the invisible forces of the universe.  

so this drive has been (A) fine, (B) partially corrupt, (C) utterly corrupt, and (D) fine again, all without apparently doing anything to it.  

relieved, but confused. :confused: :D

---

### Post by linuxopjemac on 2011-04-12
good to hear you got it solved :)

---

