---
title: "Running programs in live cd"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by carlc75 on 2007-05-24
Just a thought  as to whether this will work.

I'm running a laptop which has no harddrive(currently waiting for new one to be delivered) and am running completely off live cd and pen drive. I manually downloaded the packages for VLC and when try to ./configure it spits out a can't make executables line and something about gcc. 

Is this a fundamental problem or a noob one? :P

Carl

---

### Post by Hobo Joe on 2007-05-24
Try doing it through Automatix.

---

### Post by atoponce on 2007-05-24
Pull up a terminal, and install from apt, rather than source, and don't use Automatix.

```
sudo aptitude install vlc
```

---

### Post by carlc75 on 2007-05-24
Have no internet connection as well for the laptop, as will be on train so every time I run it wont it be wiped?

---

### Post by atoponce on 2007-05-24
Yes, it will be wiped.  That's the drawback to LiveCDs.  You can setup partitioning with your thumbdrive, so every time you install packages, you can keep them upon reboot, but I don't know how to set this up.

---

