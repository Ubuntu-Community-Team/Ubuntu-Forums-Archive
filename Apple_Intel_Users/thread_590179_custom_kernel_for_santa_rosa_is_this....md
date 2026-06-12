---
title: "custom kernel for santa rosa: is this..."
date: 2007-10-24
forum: Apple Intel Users
---

### Post by willnight on 2007-10-24
something available for download? or would that be some kind of legal issue (for someone to post so others can download, that is)?

according to this post:

[http://ubuntuforums.org/showthread.php?t=578698&highlight=santa+rosa](http://ubuntuforums.org/showthread.php?t=578698&highlight=santa+rosa)

the person "nikitvfx" has a custom kernel made for his/her santa rosa, with only a couple of things unresolved. i'd love to download and use that kernel.

i've got 7.10 installed and the fixes and patches are driving me nuts! i can't keep up with it, going through 50 million posts on the web.... (sigh) i just wanna use the damn thing, not fudge with it. i'm sure there are those of you out there who love to hack at it (and are *so* amazing at it). my kung-fu isn't in that department,  is all.

any contribution is appreciated!

---

### Post by cyberdork33 on 2007-10-24
what is it that you need to customize? what are you seeking to do?

---

### Post by willnight on 2007-10-25
i want to get the following working:

- sound
- isight
- mount and rw my mac volume (triple boot)
- hibernate

and some other stuff i can't think of right now... thx

---

### Post by cyberdork33 on 2007-10-25
> **willnight said:**
> i want to get the following working:

- sound
- isight
- mount and rw my mac volume (triple boot)
- hibernate

and some other stuff i can't think of right now... thx

You have to compile ALSA separately as alsa in the kernel does not yet support your system. See the Santa Rosa thread.

isight support is already in gutsy, out-of-the-box. There is a bug in gstreamer though that prevents it from working at full resolution. Fixes are on the way. (not a kernel issue)

mounting hfs+ is already enabled in the kernel and has been for a long time (you have to turn jounaling off in OSX)

Suspend / Hibernate is a tough one. I doubt there is a conclusive solution to even get that to work at all yet. Using an older kernel (from feisty) will work for those using ATI, but I am not sure what stops you on Santa Rosa. A custom kernel *might* fix this, but I don't know what option would need to be changed.

---

