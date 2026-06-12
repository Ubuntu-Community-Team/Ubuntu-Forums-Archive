---
title: "permission denied?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by amidamarux on 2007-03-03
I have googled this for about 2 hours trying anything but nothing is working, so I was wondering if anyone here could help me:
I just got kubuntu installed on a portion of my Hd and am dual booting with Windows Xp media center, and  I want to listen to my music on the windows drive,I have it mounted but every time I click into the hd portion windows is on it says access denied, not enough permissions, I have tried Chmods, and everything, but it isn't working, so how do I get permission to access the windows portion, or atleast my music.

---

### Post by aysiu on 2007-03-03
You don't *chmod* a Windows partition. You just mount it properly.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by taurus on 2007-03-03
How did you mount it?  What's the output of this command from a terminal?

```
df -h
```

---

### Post by amidamarux on 2007-03-03
> **aysiu said:**
> You don't *chmod* a Windows partition. You just mount it properly.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

wow, I tried this once, but I guess I did it wrong, ty for the help, now  Ican get to everything, but  Ihave one more question, will it do this automatically when I log on? or do ihave to do this everytime I reboot?

---

### Post by aysiu on 2007-03-03
It should do it automatically from now on every time you boot up.

---

### Post by amidamarux on 2007-03-03
> **aysiu said:**
> It should do it automatically from now on every time you boot up.
okay ty, so kaffeine should play mp3's, but it isn't working, sorry for the trouble, got a link on how to fix that?

---

### Post by aysiu on 2007-03-03
This link may help, but I've never tried to play MP3s with Kaffeine before.
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

