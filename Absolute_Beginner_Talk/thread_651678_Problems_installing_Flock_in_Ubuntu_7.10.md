---
title: "Problems installing Flock in Ubuntu 7.10"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by rgraves on 2007-12-27
Why do I keep getting this error message when I try to install Flock. These instructions are from the Flock web site.

Bob



rag@rag-desktop:~$ tar -C /home/rag -xzvf flock-1.0.3.en-US.linux-i686.tar.gz
tar: flock-1.0.3.en-US.linux-i686.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by taurus on 2007-12-27
Where did you save that file, flock-1.0.3.en-US.linux-i686.tar.gz?  Perhaps you saved it to your Desktop which means you need to change to that directory first before you try to unpack it.

```
cd ~/Desktop
tar xvzf flock-1.0.3.en-US.linux-i686.tar.gz
```

---

