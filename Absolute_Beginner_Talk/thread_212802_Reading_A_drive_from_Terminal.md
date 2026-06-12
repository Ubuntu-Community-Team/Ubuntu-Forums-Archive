---
title: "Reading A drive from Terminal?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by darkwarrior0404 on 2006-07-10
How do you readfiles on the a drive from the terminal? I've tried cd A:\ but nothing is really working, thanks a lot for your help:confused:

---

### Post by echo $USER on 2006-07-10
the code is > cd /media/fd0 it think.

---

### Post by darkwarrior0404 on 2006-07-10
cd /media/floppy I figured it out, thanks a lot tho, the /media hinted it :D thanks!

---

### Post by Brunellus on 2006-07-10
> **darkwarrior0404 said:**
> How do you readfiles on the a drive from the terminal? I've tried cd A:\ but nothing is really working, thanks a lot for your help:confused:
Linux is NOT windows or DOS.  Physical disk devices are 'mounted' onto points in a large, unified file system--a hierarchy of directories.  Note that the directory separator in Linux is a FORWARD slash / and not a BACK slash \ (which has a very specific use, but I won't get into that here)

Ubuntu mounts removable media in /media/ 

If you're going to be working in the terminal, read up on bash commands:

[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)

---

