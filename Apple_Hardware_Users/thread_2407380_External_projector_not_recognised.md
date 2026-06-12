---
title: "External projector not recognised"
date: 2018-12-03
forum: Apple Hardware Users
---

### Post by koldrakan on 2018-12-03
I have a MacBook Air 2011 running Ubuntu 16.04 with the Mate desktop environment (not Ubuntu Mate). 

Using an Apple VGA adapter I can use an external monitor without problems, I just have to plug it in. But when I connect a projector with the same adapter it doesn't work. I have tried with the built-in tools and also with arandr and xrandr, but it just does not see the projector. 

What else can I try?

---

### Post by TheFu on 2018-12-03
Force the resolution to be a standard for the projector, 60Hz.  If that doesn't work, there are some projectors which just don't work with computers.  Check the projector-centric home theatre forums.

You didn't mention the length of the cables.  My projector refused to work with some cables that were over 10ft, but worked fine with 6ft cables.  I did some research and found a reputable, very thick, cable which has been working for almost 10 yrs now.  My projector supports HDMI, so I use that.

---

### Post by koldrakan on 2018-12-04
Thanks, I'll try that. This projector should work though, since it is in a seminar room and people connect to it all the time with the same cable. However, it is over 10 ft.

---

### Post by TheFu on 2018-12-04
ah ... using standard resolutions 1280x720 @ 60Hz will fix it.  Or 800x600 if the machine is really old.
lxrandr easily controls that.  I use it all the time when giving presentation at the local University.

---

