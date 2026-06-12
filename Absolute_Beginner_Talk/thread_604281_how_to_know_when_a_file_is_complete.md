---
title: "how to know when a file is complete"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-11-06
Hey!

I have a general linux question... how do i know when a file has finished being created? Id like to poll a directory with FIND/EXEC to move completed downloads to specific places when they have finished downloading. The trouble is that when a download starts it creates the file and FIND has no idea if the file is finished or not.

Id just like to move completed files to different places based on file type.

Can someone suggest another way to achieve what i want?

---

### Post by phiphedog on 2007-11-06
You could use the -mmin or -mtime option that looks for files that were last modified minutes or days ago respectively. For me, usually if a file that is downloading hasn't been modified for 24 hours then I can safely assume that it is finished. It could be risky if your download isn't finished and is waiting for sources.

---

### Post by SpiritIsReality on 2007-11-06
howdy
I think what could work is tail.
I mean man tail.
```
tail -f filename
```
is supposed to follow along in the terminal and show you the appended data as the file grows.
```
man tail
```
haha! hope it helps.
trails

---

### Post by daengbo on 2007-11-06
How are the files being downloaded? By wget? Firefox? Bittorrent?

You can use fuser to identify the process on the file, then use wait <process #> until the process finishes.

Hope that starts you off.

---

