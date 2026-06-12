---
title: "rm has no effect on disk space"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by kerryhall on 2008-02-25
Help! I have been happily enjoying Edgy, when today Firefox crashed. df showed me that there was 0 bytes free, the cache must have used up all my free space. (Even though I set disk cache size in about:config to zero!) I tried going to my home folder and removing a few files I didn't need, and to my horror rm removed the file but no space on the disk was freed. After rebooting, X could not start, and there was still 0 bytes free, and rm still has no effect on disk space.

Ideas? Thanks!

---

### Post by wirelessmonkey on 2008-02-25
What, exactly, did you rm? i.e. What command?
Assuming your system is functional, try sudo apt-get autoremove to get rid of all your old .debs

post the output of :$df -h

---

### Post by kerryhall on 2008-02-25
I just rmed some of my personal files...a few pdfs that I had that were a few MB in size each. It should have freed up 10 MB or so. The files were removed, but no space was freed.

autoremove freed up 2 megs or so. Which is good, but it doesn't fix the problem with rm.

thanks!

---

### Post by kerryhall on 2008-02-25
bump

---

### Post by yuv656 on 2008-05-04
I have the exact same problem. Free space stays at 0 no matter what. Please help.

---

### Post by halfhaggis on 2008-05-04
You probably have some runaway process that is spewing out log files.

Let's see where all the space is getting used up. Submit the output of:

```
sudo du -h --max-depth=1 /
```

This will show us which directory is using the most space -- it may take a while because it needs to scan the whole drive.

If you have a flash drive, you might be able to move files to it (with 'mv' command) and so free up space, but if we don't find out what is using up the disk space, it'll just happen again.

---

