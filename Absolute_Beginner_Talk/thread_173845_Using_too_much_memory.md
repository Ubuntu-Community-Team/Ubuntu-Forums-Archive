---
title: "Using too much memory"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-11
I have a p.o.s. system with only 256k memory.  Today I installed Drapper along with the KDE envi.  After the install I was playing around with it, and I realized that it was running at a snails pace, much slower than it did with Breezy & Gnome.  I looked at the processes and it said that I was using 253 MB of memory.  The only thing I had running was Gaim!!  So I shut down a few programs in the taskbar that were automatically running, as well as Gaim, and I'm still using 246 MB.  Is there any way to make it so I'm not using so much memory, or am I basically screwed?  Thanks in advance for any suggestions you might have.

---

### Post by nanotube on 2006-05-11
well, kde is pretty memory-hungry, that's just the way it goes.
for a speedier system, you might want to try xubuntu (xfce) instead of kde.
```
sudo apt-get install xubuntu-desktop
```
should get you the xfce option in the sessions menu on login.

---

### Post by brady618 on 2006-05-11
I'll try that.  I really like the way KDE looks, though, as opposed to Gnome.  How does xfce look in comparison?  Also, I noticed that there are lots of things running in the processes that appear to be programs.  Would I be able to kill katapult and knotify, for example, and keep the system stable?  Is there a place where I can see a list of all the files that need to be running for the system to remain stable?

---

### Post by aysiu on 2006-05-11
If you want KDE to use fewer resources, paste these commands into a terminal ```
sudo apt-get update
sudo apt-get install kpersonalizer gksu bum
gksudo bum
kpersonalizer
``` When BUM loads up, uncheck all the boxes you don't want. When KPersonalizer loads up, choose "fewer effects." Leave only "background wallpaper" and "image previews" checked.

---

### Post by brady618 on 2006-05-11
Sweet.  Thanks aysiu, I knew something like that had to exist.  I'll post back with results once it's done.

---

### Post by brady618 on 2006-05-11
Hmm... it worked kind of, but there wasn't a HUGE difference.  Any other fixes that a n00b could perform which might help me solve my problem?

---

### Post by aysiu on 2006-05-11
I have 128 MB RAM system that runs fine with KDE. Maybe it's Dapper not playing nice with your computer (you said you had Breezy on there before?). I'm not sure what it is.

I will say this, though: KDE is my preferred desktop environment, but Xubuntu looks really slick in Dapper. The splash screen is cute, the default theme is glassy and modern-looking, and they changed up the Rox-Filer file browser for Thunar.

Try ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` Log out, select Session > XFCE, log back in. See how you like it. If you don't, just go back to KDE and ```
sudo aptitude remove xubuntu-desktop
```

Be sure to use *aptitude* and not *apt-get*.

---

### Post by brady618 on 2006-05-11
One more ? .  I am currently using Opera b/c I absolutely LOVE Opera, and it works phenominally on my other PC, but it is a big program and can be a memory hog at times.  Is there a smaller more lightweight browser that I can use in KDE, other than firefox and Konqueror?  Also, is there a less memory consuming IM program than Gaim (I really don't like Kopete.)  Thanks

---

### Post by loell on 2006-05-11
Ubuntu + a decent wm + with all the presets
would be nice.. i just wish there is one..

---

### Post by aysiu on 2006-05-11
Try Epiphany.
It's not native to KDE, but it's still rather lightweight.

If you don't mind a browser that's light on features, you may want to try Dillo, too--which is even more lightweight than Epiphany.

---

