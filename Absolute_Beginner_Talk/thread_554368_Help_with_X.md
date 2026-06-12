---
title: "Help with X"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by nyorondesu on 2007-09-18
Okay, I was fiddling around with trying to fix the resolution on my laptop to 1440x900 by running dpkg-reconfigure xserver-xorg, but after two restarts I found it wasn't working [in fact, my resolution had fallen to 1028x768]. I noticed that some other things weren't working either (ie, Beryl), and I looked and I noticed that the NVIDIA Restricted Driver was no longer in use, so I set it back to be used, and it called for a system restart. However, upon restarting my system, I get an X error, and I can only run in failsafe mode (ie, terminal only), and nothing I can think of will fix this. Anyone have a viable solution to this?

---

### Post by nonewmsgs on 2007-09-18
dpkg-reconfigure xserver-xorg
again and change your resolution
if it still doesnt't work try driver vesa and then try running envy

---

### Post by nonewmsgs on 2007-09-18
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

for envy

---

### Post by sumguy231 on 2007-09-18
Also, dpkg-reconfigure xserver-xorg does back up your last (working in this case) configuration, so you can get back to a working state by copying the backup:
```
sudo cp /etc/X11/xorg.conf.YYYYMMDDHHMMSS /etc/X11/xorg.conf
```
You'll need to find out the YYYYMMDDHHMMSS part by looking in /etc/X11:
```
ls /etc/X11
```

---

### Post by nyorondesu on 2007-09-18
Okay, running vesa and trying Envy worked perfectly. Not only is everything stable and working again, but I also got my 1440x900 res.

Thank you very much~~!

---

### Post by nyorondesu on 2007-09-20
Okay, I have one more quick problem that has arisen from solving this issue. It seems that all my title bars on all my windows have disappeared, and I have no idea how to get them back. Anyone here know?

---

### Post by Dr Small on 2007-09-20
I had this same exact thing happen to my account once.
I had to make another account to get the window borders back, as I could not get them back any other earthly way...

Dr Small

---

