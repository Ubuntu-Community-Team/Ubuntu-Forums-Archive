---
title: "Use another partition for sharing on dual-boot systems?"
date: 2007-01-07
forum: Apple PPC Users
---

### Post by Gen2ly on 2007-01-07
I just got done attempting to create a shared folder on OS X partition -  I dual-boot Ubuntu and OS X and need some files accessible by both systems -  but had no success.  Here's what I did:

> sudo mkdir /mnt/MacBook_OSX
sudo mount /dev/sda2 -t hfsplus -o rw /mnt/MacBook_OSX

I try to copy anything to this partition and I get:

> Read-only file system

I tried chmod ing and the results were the same.

This is where I hope the bonus comes in.  I have actually triple partitioned.  I had thought one day I'd buy Windows and put it on the third partition.  But I just found out a couple days ago that Wine will actually run the Windows programs I really want.

So... if I can't figure out how to create a shared-folder between these two systems, I could possibly use this third partition for sharing?  Anybody had any experience or thoughts?

---

### Post by didg on 2007-01-07
Hi,

Double check that journaling is not enabled, (message in /var/log/syslog after the mount command or with OSX disk utils) , If yes you have to disable it with OSX disk utils.

---

### Post by Gen2ly on 2007-01-07
> [17200733.376000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.

Of course!  That hit the nail...  
I never thought of it and I do spotlight all the time.

Actually, I'm thinking since mounting ext3 files systems on Mac OS X is kinda glitchy, I'll use that third (unused) partition for sharing between both OS's.  I seem to remember viewing somewhere that a FAT32 partition works good.  Both Ubuntu and Mac OSX can read and write from it good.  Has someone tried this?

---

### Post by didg on 2007-01-08
I'm using hfsplus but I don't dualboot often and don't use it a lot.

Issues with hfsplus on linux:
- no journal.
- can't rename  a file if changing only the case.   
- mabe slower.
- For drives not unmounted cleanly (and ubuntu doesn't seems to  always unmount hfsplus volume even with a normal shutdown) you have to get and compile Apple fsck tools or you're back to the read only case.

issue with fat32
- 4 GB limit
- more invalid characters 
- have to manually deal with resource fork ._xx files on the linux side.
- no journal.

---

### Post by Gen2ly on 2007-01-08
didg, do you mean that you're using hfsplus as your root-partition?  If that's true you are truely brave.

thanks for the info on FAT32, I never thought about the limited characters of FAT32, and I didn't know about the 4 GB limit.  My third partition is 16 GB, I think.

Maybe I'll use UFS(?)? I think that was OS X's original file system.

---

### Post by Gen2ly on 2007-01-08
Bah, just read UFS is proprietary to Apple only.  I could make this partition HFSplus and then turn off journaling?  How would I do that?

Just the one partition that is.

Oop, think I found my answer:

[Mac OS X: About file system journaling]("http://docs.info.apple.com/article.html?artnum=107249")

---

