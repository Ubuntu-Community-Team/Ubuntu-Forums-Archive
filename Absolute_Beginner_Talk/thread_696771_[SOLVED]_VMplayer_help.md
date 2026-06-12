---
title: "[SOLVED] VMplayer help"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-14
well every time i try to install it it give me this error

~$ tar xzvf VMware-player-2.0.2-59824.i386.tar.gz
tar: VMware-player-2.0.2-59824.i386.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kyle@kyle-laptop-Ubuntu:~$ 


this is the step i get to and i cant get past it even if extract it myself

---

### Post by jordanmthomas on 2008-02-14
```
pwd
```
Where are you?

Also, where is this file?  If it's on your desktop, then you'll need to 
```
cd ~/Desktop
```

edit
by the way, your error is that tar cannot find the file you are trying to extract, probably because it is not in the current directory.

---

