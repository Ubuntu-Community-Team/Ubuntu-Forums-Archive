---
title: "Sound stopped working, IEC958 light turns on instead of sound playing"
date: 2011-01-30
forum: Apple Hardware Users
---

### Post by alas-poor-yorick on 2011-01-30
The sound stopped working on my Macbook Pro 1,1. It was working fine before, and I can't think of any changes I made that would make it stop working. I know it's not a hardware problem because the Apple sound plays when I turn on the computer. Everything is unmuted in ALSA Mixer. None of the hardware options in Sound Preferences produce sound. Plugging in headphones or speakers does not solve the problem. I'm using 10.10.

One curiosity: Whenever I do something that would normally cause sound to play, the optical audio red light in the headphone jack turns on, but no sound plays.

Does anyone have an idea of what is wrong? Thank you.

---

### Post by deruberhanyok on 2011-01-31
Hello Yorick,

Did you happen to run update manager recently (within the last ten days or so) and install the available updates?

My IEC958 output also stopped working within the last week or so. However I'm using a self-built PC with an Intel motherboard (DH57JG).

My theory is that a recent update - not sure which one - may have broken something related to digital audio output. While I was trying to find a possible cause for the problem I found this:

[http://ubuntuforums.org/showthread.php?t=1677903](http://ubuntuforums.org/showthread.php?t=1677903)

Which mentions a recent kernel update for 10.04. I'm wondering if perhaps one of the recent kernel updates for 10.10 might have had a similar problem.

---

### Post by deruberhanyok on 2011-02-01
Yorick,

I've just gotten the chance to try booting my system to a 10.10 install disc and found that my optical output is definitely still working.

I've posted about it [here]("http://ubuntuforums.org/showthread.php?p=10419597") and hope to have it narrowed down quickly to submit a bug report to launchpad and get the problem fixed.

---

