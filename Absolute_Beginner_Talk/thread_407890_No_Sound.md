---
title: "No Sound"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by jasrog on 2007-04-12
Does anyone know how to get sound working in feisty 7.4? I have had sound in the other releases of ubuntu.....

---

### Post by caffienefree on 2007-04-12
Please type alsamixer into the terminal, and check whether nothing is muted and that volume is up.

Also, this guide may be of interest.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by jasrog on 2007-04-12
when I typed alsamixer in terminal i get 00 in master and 100 for pcm i see nothing muted.......

---

### Post by annda on 2007-04-12
have you tried raising the master level? if master is 00, there is zero sound...

---

### Post by jasrog on 2007-04-12
how do you raise mm or master volume level?

---

### Post by caffienefree on 2007-04-12
Go to the one that's at 0 (The title will be orange) and press up.

Also, if it's saying MM right now, it means that it's muted. Press m while it's selected and you should see the MM change to OO.

---

### Post by annda on 2007-04-12
here is how you deal with alsamixer:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsamixer](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsamixer)

---

### Post by jasrog on 2007-04-12
ok i have master unmuted showing 00 but pressing up does not raise it...how do i raise master volume?

---

