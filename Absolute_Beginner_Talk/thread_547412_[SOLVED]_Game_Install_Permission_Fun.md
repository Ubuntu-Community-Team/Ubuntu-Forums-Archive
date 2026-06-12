---
title: "[SOLVED] Game Install Permission Fun"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-09-10
Okay... Game is UT2004, but the problem is likely that I've installed it to a FAT32 secondary drive.

So, permissions are read&write, but not execute.

The trouble is that when I go in with 'sudo nautilus' or 'sudo konqueror' I still cannot set the initial script file 'ut2004' to executable. Why not? I should be able to do that, shouldn't I?

While I'm asking, should I also set the whole game directory to executable, once I learn how?

Here's the fstab

/dev/hdd1 /home/o/Thorax vfat rw,user,fmask=0111,dmask=0000 0 0

---

### Post by ofb on 2007-09-10
Right, I guess I can't change things via sudo because I can't override fstab. So I've changed that line in fstab to this

/dev/hdd1 /home/o/Thorax vfat umask=0000 0 0

I'm always nervous about this sort of thing because I don't understand the syntax in detail. (For instance, what was the "rw" doing in there? Didn't the dmask and fmask take care of that?)

What I've done, I believe, is make the drive rwx for everyone. Which is fine by me - this is a single-user home computer, and Windows is on another drive entirely. Thorax is just extra space for both systems. Hence I can't see the harm in rwx.

However I'm not going to mark this thread as 'Solved' yet, so people will have a chance to add corrections and cautions.

(Oh, yes -- the game runs fine now. I'd forgotten how fast it is, and how rusty I've become, so back to it.)


EDIT- no comments after a day, and the primary issue is cleared up, so I'm marking this thread Solved and moving on.

---

