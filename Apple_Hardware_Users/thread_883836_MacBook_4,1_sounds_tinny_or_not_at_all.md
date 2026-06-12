---
title: "MacBook 4,1 sounds tinny or not at all"
date: 2008-08-08
forum: Apple Hardware Users
---

### Post by ecormier on 2008-08-08
Here's what I've got:
it's a new macbook core 2 duo (4,1)

"lspci | grep -i audio" returns:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

"grep Codec /proc/asound/card0/codec#*" returns:
 Codec: Realtek ALC885

Now here's the problem.....from a fresh install of Hardy I get no sound at all but by adding:
options snd_hda_intel model=mbp3
to my /etc/modprobe.d/options
I can get sound but it's very tinny (no bass whatsoever.....so now my mac sounds like a $5 battery operated am radio)

I've read in other places that I need to turn up and unmute my "surround" channel....only problem is when I added the "mbp3" line to my modprobe options file the surround channel disappears

I've played around with other models which give me the surround channel, but none give me sound except for mbp3

I rarely ask questions and like to google for information, but I keep banging my head against a brick wall on this one

And I have tried this on the stock hardy alsa (1.0.15 and 1.0.16) and I even tried it on 1.0.17 (which I compiled myself) 

No luck anywhere...please someone..... help

Eugene

edit: I assume this is a bug in Alsa

---

