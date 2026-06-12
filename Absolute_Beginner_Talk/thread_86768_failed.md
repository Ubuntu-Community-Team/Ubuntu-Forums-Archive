---
title: "failed"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by emo on 2005-11-06
root@ubuntuemerson:/home/emerson # tar xzf amule-2.0.3.tar.gz
tar: amule-2.0.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



I don't know what's going on but I can't install any package using command line....this really doing my head sorry guys for keep ask the same question several  times, I have  the package on my desktop but unfortunately I can't install it.

---

### Post by Teroedni on 2005-11-06
if you have it on Desktop you must do write

cd Desktop


it should be 
root@ubuntuemerson:/home/emerson/Desktop#

---

### Post by kori.mendocino on 2005-11-06
$cd Desktop, then $tar xzf amule

---

### Post by sterrac on 2005-11-06
```
sudo apt-get install amule
```
I tried and it worked, possibly you need to add repositories to /etc/apt/sources.list

---

