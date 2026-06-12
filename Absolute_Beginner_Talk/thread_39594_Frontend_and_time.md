---
title: "Frontend and time"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by ~J~ on 2005-06-05
Hi everyone,

This is my first post and the first time I've loaded linux onto my system, so if it's a dead-easy answer, then go gentle with me.... ;)

The installation went perfect.  I've a dual booting system, and have installed Hoary Hedgehog with no probs.  First impressions are very favourable and my sole purpose of installing linux was a 'nicer' web experience and a faster OS.  Ubuntu was recommended time and time again and I've no regrets.

There are many many questions I have, but I'm finding it fun learning myself and so won't ask the obvious ones but there are 2 which have bugged me for days now and I can't see to find an answer anywhere.

Firstly, the frontend.  I was recommended KDE, people saying it's nicer than Gnome, and whilst it certainly looks better, I'm finding either slower than gnome and not very consistant.  For example I often have to press a button twice for it to register, or when I load a program, the 'bouncing icon' seems to bounce a long time, then disappears, then nothing happens!  There are some occasions when I want to change something, it asks for the root password, I enter it, and again nothing!

So is it something I'm missing, or is KDE a little 'buggy' at the moment?

GNOME does look a lot nicer, but one thing KDE has that I miss in GNOME is the RSS feed in the tasktray(?), it works perfect!  Is there anything similar for GNOME.  I have been looking at kde-look.org and was wondering if there's a similar site for GNOME.

Finally, and this is the most serious and most annoying thing, and that's the time in my system.

At the moment, it's 22:37GMT.  If I load into Ubuntu, the time says 23:37, and there's no way I can change it!  Everytime I try to, I'm asked for the root password, I enter it, and nothing happens.  I can change the date, but not the time!

Again, is it something simple I'm doing wrong, or is it a little more complication then I first thought?


TIA

---

### Post by betrayed on 2005-06-05
Well I don't know if you have updated to the current version of kde which is 3.4.1 that fixes quite a few problems I had with kde.  As for the kde-look site you can goto the sister site, [www.gnome-look.org](www.gnome-look.org)

---

### Post by betrayed on 2005-06-05
For the news feed you could use rssowl or Yarssr. I have used and prefer Yarssr but to each there own.

For the system time problem Edit the file /etc/default/rcS and change the line reading UTC=yes (or just UTC=) to UTC=no. Reboot and adjust the time

```
sudo gedit /etc/default/rcS
```

---

