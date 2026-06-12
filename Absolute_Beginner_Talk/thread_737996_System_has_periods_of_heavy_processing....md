---
title: "System has periods of heavy processing..."
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Izobalax on 2008-03-28
Hi!

I've noticed, for the past few weeks, that my system has periods of heavy harddrive accessing, which usually causes the mouse to stutter along the page/music to stutter-skip/videos to do the same etc. It's getting to the point where it's severely slowing down the work I can do on this computer and I wants to fix it. 

My system spec is in my sig. I use GNOME with the PekWM windowmanager. 

Please help.

/izo\

---

### Post by StOoZ on 2008-03-28
could be that you are running something in the background , like a virtual machine or something?

---

### Post by Trail on 2008-03-28
Keep a task manager open while you have the heavy processing and see which process is the cause for that?

---

### Post by Izobalax on 2008-03-28
Thanks for the replies, guys.

> **StOoZ said:**
> could be that you are running something in the background , like a virtual machine or something?

Nope, nothing like that. 

> **Trail said:**
> Keep a task manager open while you have the heavy processing and see which process is the cause for that?


What should I look for? The memory usage?

/izo\

---

### Post by metalpancake on 2008-03-28
yeah, i'm getting a similar problem, although in mine the hard disk is constantly being accessed, and nothing suspicious is showing up in task manager. processor levels are pretty normal though.

---

### Post by Trail on 2008-03-28
Look for CPU usage (either user or system).

Also, just an idea, maybe it's the indexing service thingy that keeps track of your files for fast searching?

---

### Post by tgalati4 on 2008-03-28
>sudo apt-get install htop
>htop

---

### Post by LowSky on 2008-03-28
> **Trail said:**
> Look for CPU usage (either user or system).

Also, just an idea, maybe it's the indexing service thingy that keeps track of your files for fast searching?

that is what it sounds like to me... turn off indexing and the issue will stop

---

### Post by tgalati4 on 2008-03-28
>ps -ef | grep trackerd

or

>ps -ef | grep beagle

---

### Post by unclejac on 2008-03-28
Yeah, maybe check this thread out: 

[ **trackerd? **]("http://ubuntuforums.org/showthread.php?t=591867")

Could be what is causing it.

---

### Post by Izobalax on 2008-03-28
> **Trail said:**
> Look for CPU usage (either user or system).

Also, just an idea, maybe it's the indexing service thingy that keeps track of your files for fast searching?


Well, my processor graph shows near 100% all the time.

> **tgalati4 said:**
> >sudo apt-get install htop
>htop


I did that and a process table but I don't understand it.

> **LowSky said:**
> that is what it sounds like to me... turn off indexing and the issue will stop

> **unclejac said:**
> Yeah, maybe check this thread out: 

[ **trackerd? **]("http://ubuntuforums.org/showthread.php?t=591867")

Could be what is causing it.


OK, I checked it out, but I don't have Indexing Preferences option. I also don't have tracker in my sessions.

> **tgalati4 said:**
> >ps -ef | grep trackerd

or

>ps -ef | grep beagle

What do these do and what am I looking for?

/izo\

---

