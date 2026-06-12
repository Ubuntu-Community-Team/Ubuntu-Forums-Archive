---
title: "Monitor change causing problems"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Paul-Henri on 2007-03-23
Greetings all,

Recently my 19" monitor died and I have had to change to a 15" one *sigh*

Problem is I had the resolution set to 1200x1024 and now I cant boot into Ubuntu as the monitor just flashes its lights at me...

I can boot into recovery mode but dont know what to do next...

Any help appreciated.

---

### Post by Muzik83 on 2007-03-23
Hey,

While in recovery mode, do a 
dpkg-reconfigure xserver-xorg

This will ask you basic questions about your video card and monitor.  If you don't know the answers to any question, then the default should work for you and you are safe just hitting next.

When this is complete, restart your computer back into the regular mode, and you should be all fixed up.

Hope this helps, and sorry you had to shrink monitors!!

-sean

---

