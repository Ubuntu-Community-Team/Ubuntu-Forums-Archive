---
title: "you tube no sound"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-10-18
hey, I am on youtube.com right now and I can't hear the sound on the videos that I'm trying to watch.  Could this be that I'm missing a certain plugin, if so which one.  Any help would be greatly appreciated.

---

### Post by r4ik on 2006-10-18
Please try,

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd

in a terminal and reboot.

Credits to xpod.

---

### Post by TheWizzard on 2006-10-18
1.sudo aptitude install alsa-oss
2.sudo nano /etc/firefox/firefoxrc
3.change FIREFOX_DSP="none" in FIREFOX_DSP="aoss"
[http://www.ubuntuforums.org/showthread.php?t=255422](http://www.ubuntuforums.org/showthread.php?t=255422)

next time search this forum first please. this issue has been discussed many times.

---

### Post by war59312 on 2007-12-30
Thanks a lot, was wondering the same thing...

---

### Post by blackind on 2008-07-23
Hello,
I have the same problem,
I did the above steps, but on step 3, a blank!! file opens named "firefoxrc", so i can't replace anything.
Any help?

---

