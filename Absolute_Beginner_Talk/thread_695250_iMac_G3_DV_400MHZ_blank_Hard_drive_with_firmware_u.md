---
title: "iMac G3 DV 400MHZ blank Hard drive with firmware update"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by guyatrandom on 2008-02-12
Could someone walk me through installing ubuntu 6.10 on an iMac G# 400mhz? It has the newest firmware update (the one you need to run OS X) and a completely blank HD. The RAM is 308 MB. When I try to boot to the disk, i hit enter at the white text menu, and it goes to the xp-like ubuntu loading deal and then nothing happens when it's done

---

### Post by dstew on 2008-02-13
Does the Ubuntu logo disappear? Do you get a white screen afterward? Do you hear any sound? Do you get a brown screen and mouse cursor but nothing else?

Some of the things that can cause the Live CD to fail include a bad CD (did you check the MD5 sum of the .iso, and burn at a slow speed, if you made it yourself?), or failure of the Live CD to run the video display properly. If you think it is the latter, you can try boot options at the beginning text screen. One to try is **live video=ofonly**

The [PowerPC forums]("http://ubuntuforums.org/forumdisplay.php?f=133") have lots of help.

---

### Post by guyatrandom on 2008-02-13
Well, the yaboot comes up. I hit enter for default, then the xp-like deal comes up, then the loading bar fills up. Then it goes to a black screen witha blinking cursor, then the cursor disappears, and then nothing. ctrl option f1 does nothing. the HDD is completely blank.

---

### Post by dstew on 2008-02-13
Did you try the boot option```
live video=ofonly
```? Also, press the tab key at the initial boot screen to look at some other options to try.

---

### Post by guyatrandom on 2008-02-13
I did all these things you mentioned. Every option did not work. CTRL OPTION F1 does nothing to y mac at all. it won't take me to a terminal.

---

### Post by dstew on 2008-02-13
Well, I am out of ideas. Maybe post on the Apple PowerPC forum. Where did you get your Ubuntu Live CD? Is it a commercial copy, or did you make it yourself?

---

### Post by dcast on 2008-02-13
I have an iMac G3 Summer Edition 2001, same problem at first, this should sort you out:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

---

### Post by guyatrandom on 2008-02-13
Sir, that command does nothing on my computer. MY IMAC DOES NOT RESPOND TO CTRL OPTION F1!!!!!!

---

### Post by dcast on 2008-02-13
Aren't there 6 terminals running simultaneously on Ubuntu, have you tried CTRL+OPTION+F(x) x=1 through 6?

---

### Post by dcast on 2008-02-13
You might also try the Alternate Install CD which will install on your iMac without the graphical interface, from there you can install the GUI and then follow the link I posted.

---

### Post by guyatrandom on 2008-02-13
well the f1 thru six did nothing

---

