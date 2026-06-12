---
title: "No XGL/Compiz?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by neilmiddleton on 2006-09-26
Am I right in thinking that we cannot install XGL/Compiz in the regular ways (i.e. How all the HOWTO's stipulate) at the moment? I've tried these and just end up with missing packages, and a very chuggy desktop.

I've noticed that a package cgwd (or similar) isn't available.  Do we have to wait until Beryl is out and about?  Am I missing something simple?

I'm running an ATI Mobility X600.

TIA

---

### Post by em3raldxiii on 2006-09-27
Hiya Neil,

I believe (and I could be wrong) that your ATI Mobility card would prefer to use AIGLX + Compiz instead.  I thought that xgl was for nvidia cards?  Dunno ... either way I have a nVidia card and XGL, so ....

Here's a thread that MIGHT be of some help:

[http://www.ubuntuforums.org/showthread.php?t=145068]("http://www.ubuntuforums.org/showthread.php?t=145068")

It's a little bit depreciated, but it should at least point you in the right direction.

---

### Post by shat on 2006-09-27
I have an X1400 and I can at least tell you how I did it.

Use the HOWTO forum here and the howto forum at [http://forum.beryl-project.org](http://forum.beryl-project.org) as well.

First, get fglrx (proprietary ATI driver) working via the howtos.  I've used the .26 and the .27 versions with success, however, your mileage may vary.  If you can type fglrxinfo and not see the word "mesa", you have succeeded.

Next, follow one of the howto's to get xgl/compiz installed.  I used [http://forum.beryl-project.org/topic-389-howto-compiz-gnome](http://forum.beryl-project.org/topic-389-howto-compiz-gnome), however, the first post states that it may or may not work until the actual release of beryl.  Sorry :(  Your best bet would be digging around the beryl forums for howtos in the meantime, however, beryl shouldnt be that long off 8)

---

