---
title: "fsck asking for root password"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by minutest on 2008-02-29
I have found how to fix this through other posts.

My question is how has this affected my PC stability and can lose files due to corruption this way? Or even sometime not be able to recover from something like this. :(

Now I tell you the story.
I have been having video driver problems currently working on another post. Anyway I swapped my LCD with a PC using an old CRT till I get drivers working on Ubuntu. Did not move anything just swapping video cords when needed.

I have dual boot with xp on my Ubuntu PC. My son and my self turned the Ubuntu PC on did not see anything on display and just turned power off to PC to check thing out. This went on for 6+ times. Found Cord or port for LCD may have gone bad in pat 24hrs.
BTW thank God for this forum as I did find a fix otherwise I would have just reinstalled Ubuntu and I have done that way to many times as a fix.

Anyway this is what came up

> * An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed. Then the system restarted. root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode. A maintenance, shell will now be started. After preforming system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
Give root password for maintenance (or type control-D to continue)

I did not know what the root password was so I rebooted using the live CD.

```
sudo passwd root
```

To reset root password.

Rebooted with out live CD

```
sudo fsck /dev/xxxx
```
xxxx=root partition

I picked Y to connect thing to /lost+found and Y to correct some ref count. There was a few other things to but I just pick Y to fix it.

Everything seems back to normal. I still have video driver trbl but will get to it (have new info from that thread and it looks promising). All files seem to be there and intact but I only checked a few.


What has this (fsck) done and is there anything that I should do after that has been ran?
:confused:

---

### Post by oldos2er on 2008-02-29
fsck is file system check, it's similar to chkdsk in dos/win. It will run automatically every 20 - 30 boots, and it will also run when the file system has not been shut down cleanly. Type "man fsck" in a terminal for more info.

---

### Post by justsomedude on 2008-02-29
I'm not sure what exactly happened there, but is it possible you have an ext2/3 driver installed on XP?

If so, it is possible it messed up the journal.

---

