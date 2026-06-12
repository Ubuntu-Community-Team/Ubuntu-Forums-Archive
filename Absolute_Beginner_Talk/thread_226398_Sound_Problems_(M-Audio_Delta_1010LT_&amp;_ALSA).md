---
title: "Sound Problems (M-Audio Delta 1010LT &amp; ALSA)"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by plotloss on 2006-07-31
Hi,

Whilst I've been using Ubuntu for a while out of curiousity I'm completely befuddled by the way it handles Sound Devices so thought I would start in the Absolute Beginner Section to try to avoid the pile of monitors under my office window becoming any larger.

I have Dapper running on a new PC with 3 M-Audio Delta Soundcards

The installer found the cards, identified them and installed them perfectly.

If I aplay --device=hw:0,0 I get sound and do so for hw:1,0 and hw:2,0

However if I try to access the output individually eh hw:0,1 or hw:1,2 then I get an error that file not found.

I've read about asound.conf/ .asoundrc in ALSA but unfortunately it leaves me more confused and the monitor flys out to the aforementioned pile.

Can anyone give me simple idiot instructions on how to extend the configuration that Dapper has autoinstalled so I can use outputs 1&2 as one stereo pair and 3&4 as the next stereo pair etc to the total of 4 stereo outputs that this card has.

I would be eternally grateful, as would my windows...

Many thanks

Matt.

---

