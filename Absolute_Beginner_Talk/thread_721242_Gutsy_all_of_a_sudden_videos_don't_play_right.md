---
title: "Gutsy: all of a sudden videos don't play right"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by inverseroom on 2008-03-11
I haven't made any changes to my system, but all of a sudden videos don't play right.  Sound is fine for all, but videos I download from the internet and play on VLC or MPlayer just give me a blank screen.  And all my own videos, I get the picture, but it displays in black and white!

This holds true for AVI, WMV, and MPG.  Last week all was well!

I installed CompizConfig and tried deselecting the streaming of vids through compiz.  No dice.  I use no desktop effects at all.

Any suggestions?

---

### Post by inverseroom on 2008-03-11
OK, switching outputs to X11 seems to have restored most functionality.  Although AVI seems to be semi-broken in VLC.  Sometimes.

Why would this have changed?

---

### Post by Arkenzor on 2008-03-11
It probably changed when you activated compiz-fusion. Many video outputs (such as gl/gl2, xvid) don't do well in a composited environment.

---

### Post by plantman on 2008-03-11
After installing updates last week, I cannot view videos. Alert says: "Video player undefined for this type of media (check Tools menu MediaPlayerConnectivity...) application/x-shockwave-flash" 
Everything was working great before the updates.:confused:

---

### Post by inverseroom on 2008-03-11
> **Arkenzor said:**
> It probably changed when you activated compiz-fusion. Many video outputs (such as gl/gl2, xvid) don't do well in a composited environment.

No, I activated compiz as a possible solution!  The problem came first.

I would imagine it was something in the last set of updates, as plantman is suggesting.  Adjusting output to x11 does seem to have done the trick...even VLC is playing AVI's fine now.

---

### Post by plantman on 2008-03-12
I had this problem some months ago and had lost (or forgot) the solution. Here it is: [http://ubuntuforums.org/showthread.php?t=621329](http://ubuntuforums.org/showthread.php?t=621329)

---

### Post by DrMega on 2008-03-12
I have the same problem. All was great, then suddenly hardly any videos worked. I haven't looked into it so I don't know why its happened, but it doesn't seem to be a localised issue if it is affecting others.

---

