---
title: "Core 2 Duo E7650"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Thacker on 2008-04-18
Which download should work with the above processor. I have seen various reports of the 64 bit working OK but my own experience is that it hangs during install; whereas the 32 bit works OK but doesn't seem to  recognise my GForce 9600 graphics card.
It's just occurred to me that that might be the reason the .64 bit hangs in the first place.
Anyone had the same problem or better still got an answer?

---

### Post by sdennie on 2008-04-18
Are you sure it's actually hanging on install?  With some cards, on 64bit the bootsplash doesn't work right (I think it has to do with blacklisted modules) so, it's possible that it's still working but, just not showing you anything on the screen until it gets to the point where it can start X (which can take several minutes).  I would check to see if the CD is still working while you think it's hanging.  Also, you could download the alternate install 64bit iso and try that instead.  It's all text-based.

Either way, you will almost certainly have to manually install the nvidia drivers if you are using a 9600 and Ubuntu 7.10.  The easiest way to do this is probably to use [envy]("http://albertomilone.com/nvidia_scripts1.html") or, you could also just install Ubuntu 8.04 which I think has uptodate enough drivers that your card will probably work.

---

### Post by stchman on 2008-04-18
> **Thacker said:**
> Which download should work with the above processor. I have seen various reports of the 64 bit working OK but my own experience is that it hangs during install; whereas the 32 bit works OK but doesn't seem to  recognise my GForce 9600 graphics card.
It's just occurred to me that that might be the reason the .64 bit hangs in the first place.
Anyone had the same problem or better still got an answer?

The Core 2 Duo is a 64bit capable processor.  I have a Core 2 Quad and I run the 32bit version but it is capable of both.

There are some incompatibilities with using 64bit but it is getting better.  I may upgrade to 64bit when Hardy comes out.

---

### Post by Thacker on 2008-04-19
Just got back - thanks for your suggestions. In answer to whether or not it's actually hanging on the 64 bit install, it gets to "running local boot scripts (/etc/rc.local)" and then stops with  the cursor flashing but no apparent cd activity; I've left it for ages with no action at all. I think I'll follow the advice given and try both flavours of 8.04.
Thanks to you both for your help - although I did build this PC myself we Silver Surfers need all the help we can get!

---

