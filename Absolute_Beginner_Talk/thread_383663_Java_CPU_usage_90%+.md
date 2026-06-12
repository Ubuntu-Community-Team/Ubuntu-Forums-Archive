---
title: "Java CPU usage 90%+"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2007-03-13
Running a java appelet like on virtualnes.com causes the java virtual machine to take 90%+ of the CPU. I have the JRE 1.6 from Sun installed, with the libjavaplugin_oji.so in /lib/mozilla-firefox/plugins ... etc. I had the same problem with JRE v 1.5.

Does anyone have ideas about this issue? From my newb perspective it seems like it could be anything.

---

### Post by brettg on 2007-03-14
virtualnes is obviously an emulator, and even though it is providing relatively simple hardware emulation, emulation is generally quite CPU intensive in most cases. This is inherant in the nature of things. I wouldn't be too concerned, it is probable that this is perfectly normal. 

I have no personal experience with virtualnes though.

---

### Post by mdecler2 on 2007-03-14
Thank you for the response brett. I actually tried using Java in other places and did not find the CPU problem.
I decided to experiment further with the virtualnes site, and I find that the emulations run very well when I turn the sound off (there is an option on the site that turns off the sound). In fact, I find that the emulations run even faster than they should at times when the sound is off. 
This does not seem so surprising, yet I wonder if there is a fix? Could it have something to do with ALSA? The site has a notice: "Please close all Media Players prior to starting a game. Failure to do so may result in system instability." Perhaps there is an issue with the emulator and the ALSA mixer?

I don't really know anything about ALSA. Does anyone have any insight?

---

