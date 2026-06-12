---
title: "Audacity input"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by venicia on 2008-01-04
"Error opening sound device. Please check the input device settings and the Project Sample Rate."
I've heard of the OSS/ALSA issues; tried every possible combination of OSS/ALSA for output/input, lowered the sample rate, changed the number of channels, etc. I do believe I've tried everything and nothing works. Anyone possibly know how to get rid of this error message so I can get some semi-urgent recordings done? 

I mean, I have Audacity on XP on my other partition that works beautifully. However, when I connect it up to my main laptop (which runs Vista Ultimate), the quality of the recordings are crap. I could technically restart my computer and boot into XP every time I wanted to record something and then transfer it to my Vista for mixing, but I would prefer finding a fix to get it working on Ubuntu.

---

### Post by CatKiller on 2008-01-05
I've not come across your particular error message, but you could try disabling ESD in System -> Preferences -> Sound -> Sounds and see if that helps. Otherwise, you could try Ardour, which looks prettier. Also, having recordings that sound crap - if the recording device isn't really crap - seems quite likely to be a gain issue. Try lowering your levels.

---

