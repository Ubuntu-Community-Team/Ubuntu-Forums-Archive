---
title: "Default out the xorg.conf file"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by jon.carstens on 2007-07-05
Is there a way to restore the xorg.conf file to its default settings?

I guess I didn't make a backup before trying to do the ATI X**** fix and now Ubuntu wont even load. When I try to load it my monitor goes blank and I get this message:

Out of Range
33.xx kHz / 30 Hz

I'm on the LiveCD right now and I can use the terminal. I just don't know what to do...

---

### Post by freebird54 on 2007-07-05
I answered on your other thread - but for this -

Boot into the 'Recovery' mode entry (you will be in text only mode) and run the sudo-dpkg command described in my other post.  This will generate a new xorg.conf for you.

---

### Post by jon.carstens on 2007-07-05
I will attempt to fix the problem in the original post first. Thanks for answering this question aswell.

---

### Post by kerry_s on 2007-07-05
if you look at the top of xorg.conf it tells you how to return to the default settings.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

