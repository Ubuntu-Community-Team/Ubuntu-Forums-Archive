---
title: "ignoring updates"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by l3f3vr3 on 2007-05-25
I recompiled ffmpeg from ffmpeg-source.  I also named the version so that it is greater than the default ubuntu one.  However, the update manager insists that I wan't to downgrade to the previous one before I compiled.

Is there a ignore list or something I can use to skip this upgrade?

---

### Post by Pragmatist on 2007-05-25
In update manager, can't you just deselect what you don't want updated?

What are the version numbers of the Ubuntu package, and the source package that you renamed?
[QUOTE=l3f3vr3]However, the update manager insists that I wan't to **downgrade to the previous one before I compiled.**
[/QUOTE]
What *exactly* is update manager doing?

---

### Post by l3f3vr3 on 2007-05-25
> **Pragmatist said:**
> In update manager, can't you just deselect what you don't want updated?

What are the version numbers of the Ubuntu package, and the source package that you renamed?

What *exactly* is update manager doing?

Deselecting works, but update manager keeps its icon on top of the screen and the update never goes away.

my version (from checkinstall setup) 0.cvs20060823-9.1ubunut5-1

ubuntu version 0.cvs20060823-3.1ubuntu4

actually I just noticed it had a 3:0.cvs  I am going to try and checkisntall agin


Ahh--changed my version to 3:0.cvs... that fixed it
   (is that a bug in ubunutus version number?)

---

