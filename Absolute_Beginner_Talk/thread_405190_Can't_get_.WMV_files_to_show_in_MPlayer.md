---
title: "Can't get .WMV files to show in MPlayer"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Sol1 on 2007-04-09
Hey guys,

I'm having trouble getting .WMV files to play in MPlayer.  I have the codecs installed, but the screen is black when playing the video.  Sounds works just fine.  Interestingly, if I drag the window around, as soon as I release it I can see the video for about 1/2 a second, but then it goes black again.  

Anybody have any suggestions for me?

Thanks,

Sol

---

### Post by mand0 on 2007-04-09
I can't tell you how to make mplayer work but if you really wanna watch that video just install VLC.  Do a search for it in "Add/Remove Programs".  It will almost certainly play it.

---

### Post by Sol1 on 2007-04-20
Hey guys,

I installed VLC but am getting the same problem.  Is this a video card issue?

I'm just using the onboard card in my PC which is the Intel 82915G/GV/910GL Integrated chipset.

Thanks!

---

### Post by marko_4454 on 2007-04-20
I am not totally 100% sure, but its because of the codecs.

You should try this in terminal:
```

sudo apt-get install w32codecs

```

---

