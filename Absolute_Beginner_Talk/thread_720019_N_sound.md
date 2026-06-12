---
title: "N sound"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by nick937 on 2008-03-09
My sound was working perfectly until I installed some updates a few hours ago, now when i try and turn up the volume i get the following error: 
```
No volume control GStreamer plugins and/or devices found.
```
when I try alsamixer I get:
```

nick@t00r:~/Desktop/alsa-driver-1.0.16$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
nick@t00r:~/Desktop/alsa-driver-1.0.16$ 

```
I also tried reinstalling the alsa drivers.
this is my  lspci -v | grep Audio:
```

nick@t00r:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
nick@t00r:~$ 

```

what do I try next?

---

### Post by hhhhhx on 2008-03-09
this happened to me too, i ended up reinstalling, (more than just that was wrong with my system), but i believe there is a thread about it somewhere around here

looking....

---

### Post by superprash2003 on 2008-03-10
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by bollix47 on 2008-03-10
It appears the latest kernel in Hardy has some sound problems.

See [this thread]("http://ubuntuforums.org/showthread.php?t=720140") .

---

### Post by NightwishFan on 2008-03-10
Just boot with the .11 kernel if you have it.

---

### Post by nick937 on 2008-03-10
thank you for your help, next time I reboot, I will boot with the .11 kernel...

---

