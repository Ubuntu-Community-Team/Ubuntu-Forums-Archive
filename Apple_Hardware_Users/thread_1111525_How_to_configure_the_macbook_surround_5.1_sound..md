---
title: "How to configure the macbook surround 5.1 sound."
date: 2009-03-30
forum: Apple Hardware Users
---

### Post by volanin on 2009-03-30
I need some help!
:)

I am having a hard time configuring the macbook surround 5.1 sound.
I am connecting it to my home theater via the optical cable plugged
into the headphone jack, but the sound output is not right.

It sounds more like a stereo sound with a subwoofer than a 5.1 surround.
And indeed pavumeter displays only 2 channels.

When I change the pulseaudio configuration to enable 6 channels by
default, pavumeter displays the 6 channels correctly, and it also displays
that the sound should be comming from the correct speakers... but I
get no sound output at all. 100% silence.

I am using Intrepid 64-bit with a Macbook 2,1.
Does anyone has any suggestions?
Thanks!
:)

---

### Post by volanin on 2009-03-31
Ok, I managed a partial solution.
Since I watch all my movies in mplayer, I just run it with:

```
$ mplayer -ac hwac3 movie.avi
or
$ mplayer -ac hwdts movie.avi
```

This passes the unmodiefied audio stream through spdif.
And the home theater plays it perfectly.


For everything else, it's still 2.0 for me.
Which personally don't bother, but is incomplete!
:)

---

