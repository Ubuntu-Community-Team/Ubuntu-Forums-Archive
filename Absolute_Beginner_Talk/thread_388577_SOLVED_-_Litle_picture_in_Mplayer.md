---
title: "SOLVED - Litle picture in Mplayer"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-03-19
Of some reason the picture in the mplayer is realy smal. i was just to lay down and watch a movie, i select aspect ratio of 4:3 and fullscreen but its not full screen its like a litle box with black around it.

What is the problem?

EDIT:

I got it. For some reason i whent into the preference and change the video setting from x11 to gl. Dont know if this is the best way but it works.

---

### Post by taurus on 2007-03-19
Go into Preferences and in Video to see which driver you are using.  Try xv.  Then, edit  ~/.mplayer/config from a terminal

Applications -> Accessories -> Terminal
```
gedit ~/.mplayer/config
```
and add this line to it.

```
zoom = yes
```
Restart MPlayer again.

---

### Post by Hutom on 2007-04-05
Thanks TAURUS.

---

