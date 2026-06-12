---
title: "totem wont play dvd"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by rwltrz4 on 2007-12-09
says it needs plugins, problems is what plugin, doesnt tell you?

---

### Post by prodigalson666 on 2007-12-09
synaptic package manager, search gstreamer plugins, look for dvd plugins.

---

### Post by SunnyRabbiera on 2007-12-09
you probably need libdvdcss, this is an easy fix:
[just go here]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/") and download a package that matches your system (if you use intel use a i386 package, if you use AMD use a amd64 package and sofourth)
the file type to download is .deb, that is the default installer file for ubuntu
installing it is quite simplistic, go here for more reading if you need it:
[look here]("http://monkeyblog.org/ubuntu/installing/")

oh yeh about gstreamer, its a bit too shaky for my tastes so I use the method above

---

### Post by prodigalson666 on 2007-12-09
the lib package is also in synaptic, totem xine did the trick for me also.

---

### Post by rune0077 on 2007-12-09
> **prodigalson666 said:**
> the lib package is also in synaptic, totem xine did the trick for me also.

Yep, you'll need Totem Xine. The Totem that ships with Ubuntu won't play DVD's, because it can't read the menus. For some reason, even through this Totem-player is not fully developed yet (but hopefully soon will be), it got include in the release anyway. Totem Xine works fine though.

---

### Post by rwltrz4 on 2007-12-09
i downloaded xine from synaptic and still no go, says it has no plugin, it also gstreamer in order to get xine.

---

### Post by vikramsharma on 2007-12-09
Just install totem-xine that should do it.  Installing totem-xine would also let you play avi files through totem.

---

### Post by warthogism on 2007-12-10
> **rwltrz4 said:**
> i downloaded xine from synaptic and still no go, says it has no plugin, it also gstreamer in order to get xine.

same problem here. it uninstalled gstreamer, but totem still says "There is no plugin to handle this movie."  it plays xvid, divx, avi, etc just fine.  only problem is the dvd.

even vlc wont do it.

---

### Post by phenest on 2007-12-12
I installed libxine1-plugins which enabled the DVD to start but it then stops with the error:
> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
..but libdvdcss2 IS installed because I can play DVDs in VLC.

What now?

---

### Post by philinux on 2007-12-12
work through this how to.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by t0p on 2007-12-12
Totem seems really shaky re dvds.  I only just installed Gutsy, haven't tried it with dvds yet; but with Feisty, after I installed the drivers, it would play some dvds but not others - it just jumped straight into movies, no menus, so I couldn't use special features - sometimes a slice would be missing off the bottom of the picture - and with many dvds, if I pressed stop then play again, Totem would say it didn't have the necessary drivers... even though it had been playing the damn thing just moments before! I'd have to restart Totem to get it to work again.

As I just said, I haven't tried to play dvds with Gutsy yet, but this thread doesn't make me hopeful.  I think I may give totem-xine a go if it's still a PITA.

---

### Post by phenest on 2007-12-12
I just tried another DVD and it played. But some of my DVDs won't play.

The one that WILL play is region 2 and the one that WON'T play is region 2+4.

Would it help if I made my drive region free?

---

### Post by t0p on 2007-12-12
> **phenest said:**
> 
The one that WILL play is region 2 and the one that WON'T play is region 2+4.

Would it help if I made my drive region free?

*Maybe*... but it doesn't sound to me like the region is the problem.  The dvd that works is region 2, the one that doesn't work is Region 2+4 - so they both should play in Region 2.  Believe me, Totem is *not* logical when it comes to not working right.  Check out my post above for proof of its illogicality!!

---

### Post by philinux on 2007-12-12
i have to agree about totem being unreliable. I use smplayer/mplayer smplayer being the gui front end to mplayer. I think totem-xine is better now too.

VLC has always been mentioned on here as very good to.

---

### Post by phenest on 2007-12-12
So what now? VLC works much better but won't work with my remote control.

---

### Post by philinux on 2007-12-12
If its infra red then go to synsaptic and try LIRC Linux Infra-red Remote Control support
This package provides the daemons and some utilities to support infra-red
remote controls under Linux.

---

### Post by phenest on 2007-12-12
It's bluetooth and works fine for all other apps. Changing the hotkeys in VLC does nothing.

---

### Post by philinux on 2007-12-12
> **phenest said:**
> It's bluetooth and works fine for all other apps. Changing the hotkeys in VLC does nothing.

You need to start another thread with correct title then. :)

---

### Post by frodon on 2007-12-12
Do you know that ubuntu have a documentation ?

Maybe some users should consider to read it from time to time, when i buy a new electronic device i always read the manual to answer my questions, you should do the same with ubuntu ;) :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by argraff on 2007-12-14
> **SunnyRabbiera said:**
> you probably need libdvdcss, this is an easy fix:
[just go here]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/") and download a package that matches your system

THANK YOU!!! After reading about 20 pages and various ways to do this - nothing was working! GPG keys, redoing the sources.list, whatever. That link made it work for me (in Totem).

---

### Post by phenest on 2007-12-18
> **frodon said:**
> Do you know that ubuntu have a documentation ?

Maybe some users should consider to read it from time to time, when i buy a new electronic device i always read the manual to answer my questions, you should do the same with ubuntu ;) :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Perhaps you haven't given a moments thought to the fact that people have read the documentation, followed the instructions to the letter, and it still doesn't work. Why else have this forum if it's in the documentation.

As it happens, Totem plays all my DVD's fine now. No extra work involved. It just started playing them for no apparent reason.

---

### Post by frodon on 2007-12-18
The instruction provided in the link works, if you follow them you will have the proper codecs installed as long as you have enabled all the repositories.

---

