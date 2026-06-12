---
title: "i found a 2 year old thread that describes how to do what i need. is it still usable?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-11-24
hey guys... i'm trying to set up my computer to let me run full-screen openGL games on my ati x300. unfortunately, i need to run XGL to get 3d acceleration  and compiz. i've found what looks like a brilliant solution on this how-to : [http://ubuntuforums.org/showthread.php?t=51486/](http://ubuntuforums.org/showthread.php?t=51486/)

but it's from 2005, and the guy who wrote it hasn't been on since september, so i can't ask him directly: will the steps work with a 7.10 build of ubuntu? how can i check?

---

### Post by -grubby on 2007-11-24
well if it's for an old version of Ubuntu than all sorts of problems can arise.
EDIT:looked at the thread and for the last version of Ubuntu Feisty (before Gutsy) than replace xserver-common somewhere with x11-common
EDIT1: to be specific here is what you do
sudo dpkg-reconfigure xserver-common chance "xserver" to "x11"

---

### Post by ijason on 2007-11-24
is that the only part of the how-to that's out to date? or thats just the one you immediately noticed?

---

