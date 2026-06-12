---
title: "A way to swap front/rear speaker channels?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by JWPMusicMan on 2007-04-24
Hi all, new to Ubuntu, but I have it set up, and everything is working nicely, including Rosegarden4.

Back over on XP, i'm using KX Audio as the driver for my SB Live Platinum 5.1.  By default that driver swaps the front and rear speakers.  Reason being, that the front speakers use the AC97 codec, and the rears use the I2S codec, which is a higher quality, from what I've read.

My question is this:  In ubuntu, how would I go about swapping the front and rear speaker channels, so that the front speaker signal is sent out through the rear speaker jack similar to KX Audio's driver?

Is there a program that can set this up?  ALSA? JACK? Or can I set this up in terminal? If terminal, what commands and values?

I've searched the forums for anything similar to this, but I haven't turned up anything (yet)
I appreciate any help, so Thanks in advance.

-James

---

### Post by kpkeerthi on 2007-04-24
run alsamixer from the terminal and make sure all the required sliders are turned on.

---

### Post by JWPMusicMan on 2007-04-24
Well, I think I've done this, but what would constitute as "required" sliders?  I see nothing labeled rear, or I2S.  I've seen the AC97 slider, but of course, that's the front speaker jack (I think)  Which slider corresponds to the rear speaker jack, and How would I go about sending the front speaker signal to the rear speaker jack? I only have 2 speakers, I don't have a 5.1 setup or anything fancy.  It's just a matter of sending the signal to the right output, so I can use the better DAC, and get a better playback response for critical listening.

I don't see how turning on the sliders would swap the channel signal. I'm not just trying to turn on the rear speaker here, I'm trying to _swap_ the front channel output to the rear channel. I wouldn't think just toggling on a slider would accomplish this task.  I think it's more routing the front channel to the rear output.

I'll look around some more.

---

