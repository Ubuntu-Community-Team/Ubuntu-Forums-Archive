---
title: "rsync via ssh has overwritten some files and I'm looking to restore them"
date: 2010-08-27
forum: Apple Hardware Users
---

### Post by l0uismustdie on 2010-08-27
Hello.  I have two disks I have been working with one on my MacBook Pro (HFS+) and one connected to a Linux machine (FAT - this is an external hard drive).  Recently I started exploring backing up my files with rsync over an ssh from my Mac to the external hard drive connected to the Linux machine.  I did this once successfully and ported all of my Mac files to the external.  However, I did something incorrectly the second time and I believe I may have done rsync in the wrong direction and it has overwritten some files on my Mac (configuration files for iCal that had events stored, an iPhone program I've been working on).  The full rsync command I used was the following:
```

rsync -avz -e ssh linux@linuxuser:/media/external/Users /Users

```
However, I was under the impression rsync wouldn't touch files that are timestamped at a newer date so even if it was copying from the linux external to the mac hard drive why would it overwrite newer files??

I have recently downloaded scalpel to try to see if I could find these files but every time I run
```

./scalpel /dev/disk0s2 -o recovery/

```
I get the error
```

ERROR: You have attempted to use a non-empty output directory. In order
       to maintain forensic soundness, this is not allowed.
Aborting.

```
recovery/ is a directory I created solely for the purpose to scalpel and is empty.  

If there is anyone out there who has any ideas that might lead me down the path to recovering some of these overwritten files I would be eternally grateful (especially the iPhone program which I've been working on for 3 months).

---

### Post by l0uismustdie on 2010-08-30
Just giving a bump here.  Anyone have any ideas?

---

