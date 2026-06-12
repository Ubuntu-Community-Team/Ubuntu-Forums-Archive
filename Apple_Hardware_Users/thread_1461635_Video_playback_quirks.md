---
title: "Video playback quirks"
date: 2010-04-24
forum: Apple Hardware Users
---

### Post by zeroti on 2010-04-24
I've been playing videos with VLC and Movie Player on a ppc machine with Lucid installed.

Whenever I play a movie in Movie Player, it flashes the first frame and then turns black unless I run it in full-screen mode.

I've experimented with a couple of formats and for most of them, there's a vertically-oriented ripple effect that makes videos look like they're playing on a tv. maybe you could get the idea if you thought of taking every-other row of pixels and then shifting them to the left or right. the only exception to this quirk is when I'm playing a .dv file in vlc, but it then the video shows up as purple and green. :confused:

I don't know if this is relevant, but this is my graphics card:

0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

thanks for any advice!

---

### Post by zeroti on 2010-04-29
I fixed the weird video effect (in vlc at least) by disabling KMS for my radeon card:

[http://ubuntuforums.org/showthread.php?t=1460926&page=2](http://ubuntuforums.org/showthread.php?t=1460926&page=2)

However, totem still gives a black screen when I play a video. Any advice?

---

### Post by zeroti on 2010-04-29
> **zeroti said:**
> I fixed the weird video effect (in vlc at least) by disabling KMS for my radeon card:

[http://ubuntuforums.org/showthread.php?t=1460926&page=2](http://ubuntuforums.org/showthread.php?t=1460926&page=2)

However, totem still gives a black screen when I play a video. Any advice?

I thought I solved the issue by turning off visual effects in Movie Player (totem), but now I'm having the same problem again... weird. ;-/

---

### Post by dheyse on 2010-04-29
I've seen this on my G3 ibook and noticed that I get the problem if I click on a video to open up the movie player.   But if I open the movie player first, then select a video it works.  I didn't notice anything different about the command lines in ps though.

---

### Post by zeroti on 2010-04-29
> **dheyse said:**
> I've seen this on my G3 ibook and noticed that I get the problem if I click on a video to open up the movie player.   But if I open the movie player first, then select a video it works.  I didn't notice anything different about the command lines in ps though.

ok, the same thing is happening for me too... thanks :)

---

