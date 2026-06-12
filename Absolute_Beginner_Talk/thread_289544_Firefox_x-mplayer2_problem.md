---
title: "Firefox x-mplayer2 problem"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by thedoors on 2006-10-31
I installed successfully Firefox 2.0..
But i have a small problem :(
I go to websites that have embeded .wmv/other video files , and i can't view them.
It tells me 'Click here to install missing plugin.'
I click and it says *application/x-mplayer-2: Nothing found*
I tried automatix, and it has the mplayer plugin for 1.5 ..
How to install the mplayer plugin at Firefox 2.0 ??
yours,
thedoors

---

### Post by Paul41 on 2006-10-31
> I tried automatix, and it has the mplayer plugin for 1.5 ..
How to install the mplayer plugin at Firefox 2.0 ??
Search in Synaptic and see if you can find the mplayer there.

---

### Post by Jagot on 2006-10-31
You'll need the multiverse repository enabled, then:

```
sudo aptitude update && sudo aptitude install mozilla-mplayer
```

---

### Post by Mr_Ada on 2008-03-08
This still doesn't work.  I have a 64-bit system so maybe that is a problem.

chris

---

### Post by Giannis68 on 2008-03-17
**[SIZE=2]Complete Streaming, Multimedia & Video How-to[/SIZE]**

**[SIZE=2]http://ubuntuforums.org/showthread.php?t=661833[/SIZE]**

close firefox on terminal type** rm $HOME/.mozilla/firefox/pluginreg.dat** 
Firefox recreates it with the updated plugin information

for me solved firefox 3b4 when i create a symbolic link  ln -s /usr/lib/mozilla/plugins/ ~/.mozilla/

---

