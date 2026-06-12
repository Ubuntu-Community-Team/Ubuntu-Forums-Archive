---
title: "External Monitor w/ a Powerbook"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by cyclopsface on 2007-02-12
Hi,

I've been searching the forums and playing with the Kubuntu configuration tools but I can't seem to get my external monitor to work.  I have a powerbook g4 12" (1.5 Ghz) and an Acer AL2216W LCD monitor.

What I'd like to do is use an external keyboard and mouse with this monitor so that I can use my powerbook as a desktop at home (like I do in OSX).

I'm not sure how much to describe what I've already tried but - I tried to use the system preferences in KDE to set up and test the ext. monitor but the best I could do is get it to light up completely white.  If I restart the computer goes into like a safety mode with just all text until I use my backup xconf file I saved before messing with the system prefs.

Any help would be really appreciated.

:)

---

### Post by wsmoser2004 on 2007-02-13
I tried to set up dual-monitors using the KDE configuration tools too...but I had about the same experience as you...:( 

Is your graphics card an ATI or nVidia?  I have an ATI card, so I know how it's done with ATI :-P.  If your card is supported by the open-source ATI driver, then you can use MergedFB which works really well for me.  You can find the wiki at [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver").  Unfortunately, I've found that it's not particularly easy to switch between single- and dual-monitors unless you don't mind changing your xorg.conf each time you switch :).

If you have an nVidia, then maybe someone else can help you...I have no experience with such things :).

Good luck.

---

