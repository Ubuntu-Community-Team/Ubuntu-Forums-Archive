---
title: "Can't download anything."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by ma_prism on 2007-12-25
When I try to download anything, like codecs and applications I get an error like "the list of applications is not available".

How do I fix this?

---

### Post by TidusBlade on 2007-12-25
How are you trying to download? Using what program or what command in the terminal?

---

### Post by taurus on 2007-12-25
Sounds like you don't have any repo open in /etc/apt/sources.list.

Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
Otherwise, go to System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure you have a check mark for everything _except_ Sources code and CDROM.  Close it and click Refresh.  Now, see if you can install anything again either with synaptic or Add/Remove.

---

### Post by wormser on 2007-12-25
applications>add/remove>preferences... make sure main, universe and multiverse are checked.

---

### Post by ma_prism on 2007-12-25
Alright I'm trying this out now.

---

### Post by ma_prism on 2007-12-25
Now I get this problem:

**The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed**


Ugh.

I'm really a n00b to all this.

---

### Post by taurus on 2007-12-25
Try installing the ubuntu-restricted-extras or look at this link for playing DVD then.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by ma_prism on 2007-12-25
> **wormser said:**
> applications>add/remove>preferences... make sure main, universe and multiverse are checked.


Alright I did this now it's updating... Will I be fine after?

---

