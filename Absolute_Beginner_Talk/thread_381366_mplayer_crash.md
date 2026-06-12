---
title: "mplayer crash"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by jwalters on 2007-03-10
Couldn't get Totem to play a dvd movie.......so I downloaded mplayer and it seemed to go ok till movie time........then as soon as it started it crashed and disappeared........

sign said.....mplayer interrupted by signal 11 in module ...........OK
another sign.....mplayer crashed by bad usage of CPU/FPU/RAM...........

any help??

---

### Post by Delvien on 2007-03-11
Type the following command into a terminal

```
 sudo aptitude install libdvdcss2 libdvdread libdvdplay0 totem-xine 
```

This should solve the problem, i would use totem over Mplayer, i have experienced nothing but problems with mplayer.

---

### Post by jwalters on 2007-03-11
OK.......I did that and a bunch of stuff dowloaded etc......I put a dvd in and tried to play it on totem. The screen appeared for a moment and disappeared..........

I went to add/remove to see movie player ........the check mark was gone and when I rechecked it I got 'cannot install totem gstreamer. this app conflicts with other installed software.....so basically it says to re install I have to uninstall what I just installed..........:-) ahhhhh!

Now what???

---

### Post by bsugianto on 2008-03-11
Do  you have ATI for your video card?
I am using smplayer to play movies, which is basicly mplayer underneath.  And I have to use gl or gl2 for my video driver, and it plays movies for about 30 minutes but then it would crash my computer.
The only thing I can do is alt-prn screen-b. :sad:
I guess I'll go with totem from now on.

---

