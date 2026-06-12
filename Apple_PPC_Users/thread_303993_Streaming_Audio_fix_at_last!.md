---
title: "Streaming Audio fix at last!"
date: 2006-11-21
forum: Apple PPC Users
---

### Post by stream303 on 2006-11-21
Finally!  Although this might be useful in the multimedia section, since it works on my G5 iMac I thought I'd toss it here first.

When streaming internet radio, Rhythmbox and other apps would stop outputting audio yet continue streaming at the end of tracks.

Get this: I really like the default stations that Ubuntu puts into Rhythmbox - I like the ambient, trance, and psychadelic genres.  Problem is, when the audio would stop, it would really harsh my groove.  (What generation AM I from?)  anyway...

To make a long story short, I changed my Audio preferences from autodetect to ALSA in every box I came across.  Shotgun approaches rarely work, but hey I did it.  (Preferences > Sound > Devices > Alsa in all the boxes)

I even set some options from the dialog that comes up when you issue this at the terminal:

```
gstreamer-properties
```

Once again, chose ALSA as the default output.

I have nothing but OGG as a codec and fortunately, HBR1 supports that!  Yeah. Ogg ROCKS!

BTW, anyone wanting lower-bandwidth ogg versions of the default stations from hbr1.com (30kb stream vs 64kb):
(Note - these seem to work when edited directly in a program and not clicked on as a link. hmmmm)


[http://ubuntu.hbr1.com:19800/ambientlow.ogg](http://ubuntu.hbr1.com:19800/ambientlow.ogg)
[http://ubuntu.hbr1.com:19800/trancelow.ogg](http://ubuntu.hbr1.com:19800/trancelow.ogg)
[http://ubuntu.hbr1.com:19800/troniclow.ogg](http://ubuntu.hbr1.com:19800/troniclow.ogg)

I got the hints for this audio fix from:

[https://launchpad.net/distros/ubuntu/+ticket/2046](https://launchpad.net/distros/ubuntu/+ticket/2046)

---

### Post by stream303 on 2006-11-21
NOPE!

Well, it looks like my success was short lived.  It turns out that the "tracks" I was so happy with turned out to be very long 2-hour or so marathons.  So back to the same problem.  I knew better than to do a magic-wand fix. :)

Open mouth - insert foot!

---

