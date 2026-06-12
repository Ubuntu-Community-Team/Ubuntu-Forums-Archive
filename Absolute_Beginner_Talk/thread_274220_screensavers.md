---
title: "screensavers"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-09
Hello!
I have a question about the screensavers. Whenever I go to look at the ones that I have (the ones that I think were preinstalled), I'm not seeing anything (as if they aren't there). Some of the ones that aren't there (and I'm only listing a few, because I don't have very many) are:

4D Hypertorus
AntInspect
AntSpotlight
ATunnel
Biof
BlinkBox
Bubble3D
BusySpheres
And a ton more.

Anyone have any ideas on what's up?

Thanks!

---

### Post by zappa on 2006-10-09
I'm afraid I don't understand what you mean. That list, those are the ones you have I suppose? Then it's ok. If not, do you still use xscreenserver in Dapper maybe?

---

### Post by blendmaster on 2006-10-09
Sorry I wasn't so specific (one of my off days I guess).
The ones I listed are ones that I don't have, and they are a very small portion of the giant list of screensavers that I don't have.
Would using X be the problem? I really don't want to get rid of X because the last time I tried to change it, I had to go through a lot of work to fix it (major problems). Though, with proper instructions (how-to site, maybe) I'm willing to give it another shot.

---

### Post by zappa on 2006-10-09
Don't get me wrong, we'll keep X ;) 
But since Dapper xscreensaver has been replaced by a native GNOME on, just called screensaver. In that one there are less screensavers included by default.

---

### Post by CatKiller on 2006-10-09
Those screensavers are all 3D ones. They won't display for one of two reasons:

1) You don't have 3D working on that computer for whatever reason

2) You don't have the extra screensaver packages installed that contain those screensavers.

---

### Post by nick06 on 2006-10-09
I also have the same thing, more than half of my screensavers do not work on mine as well.  I have no idea what the x thing is...just wondering how i might be sbke to correct this.

nick

---

### Post by Chickencha on 2006-10-09
I've had the same problem and I have some idea of the cause, although I can't say whether or not yours is the same.

On a fresh install, my screensavers worked fine.  Then I installed the fglrx driver for my video card.  3D acceleration works perfectly, but now my 3D screensavers don't work.

The only solution I've found is to replace gnome-screensaver (which is the default screensaver with Dapper) with xscreensaver.  Strangely, my 3D screensavers worked after that.  If you'd like to replace gnome-screensaver with xscreensaver, [this thread](http://ubuntuforums.org/showthread.php?t=195557) can tell you how.

If anyone has better solution, it would be welcome.

---

### Post by blendmaster on 2006-10-09
Thanks Chickencha! 
That thread got some of the screensavers working, but some of the others still say "no preview available". Plus, I'd rather stick with GNOME's default screensaver app. But still, That was really helpful for the moment!

---

### Post by blendmaster on 2006-10-09
I know it's not the "real" way of doing things, but I decided to install automatix. It gave me an NVidia driver, and now the screensavers are all working great! I'll try to figure out how I "should have" done it though.

---

### Post by CatKiller on 2006-10-09
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```isn't it?

---

### Post by blendmaster on 2006-10-09
Yep!

---

