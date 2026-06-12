---
title: "No sound volume + other"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by ttremeth on 2006-11-01
Installed 6.10 64 bit version

Could not play DVDs, installed codecs using the automated system (gui), DVD's then played but voice volume was too low and music was load on DVD's.

Turned up volumes however now there is no volume even when testing via the sound option in admn. Can't get it back, feel like a idiot windows-trying-to be convert.

Also Nvidia looks to be installed ok on my 6600GT but the sharpness does not appears as good as windows or other distros I tried.

In addition I need a media player that does digital TV for unbuntu and was looking at Kaffiene but could not find much for installing it under ubuntu or adding to the sources to install. Anyone have these details or a better all in one media player (not media centre)that can be installed via the packagemanger gui.

Lastly, I can see my USB drive formated in NTFS but not my local sata drive with xp on it. This appeared fine under su linux

---

### Post by raqball on 2006-11-01
try 

```
alsamixer
```

In terminal. this is a common problem. Once in alsamixer use the left and right arrow keys to move. If sound is (mm) muted then once in that area hit the 'm' key to unmute. make sure volumes (up and down arrow keys) are cranked in alsamixer.

Once done hit 'esc' ket to exit

---

### Post by ttremeth on 2006-11-01
Thanks so much!. Any suggestions on the other stuff

---

### Post by ttremeth on 2006-11-01
Any suggestions on theo ther stuff?

---

