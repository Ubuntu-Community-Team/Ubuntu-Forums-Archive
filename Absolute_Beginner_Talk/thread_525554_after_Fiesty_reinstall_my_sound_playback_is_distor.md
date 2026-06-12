---
title: "after Fiesty reinstall my sound playback is distorted"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-08-14
My sound was fine for months until my hard drive broke and I had to put an old hard drive in and reinstall Feisty. 

Now on playback I get intermittent crackling, a bit like a loose wire in fact but its not that because the same system in windows is fine. Mp4's files from my phone and DVD's don't seem to be affected on playback but CD's and recorded CD files are. 

I am not a complete beginner on Feisty but I am where this issue is concerned!:confused:

I have tried > System > Preferences > sound and on the driver test sound I do not get a problem

Any ideas?

My sound card is an old creative labs sound blaster and im using ES1370 [AudioPCI] driver (at least I think this is a driver????) and prior to re installation of system I was using this.

---

### Post by Bagster on 2007-08-14
This happened to a friend of mine - his music sounded distorted in loud passages. His problem was caused by the alsa driver sending a too high signal level to the sound card causing it to overload and crackle. I dont know if this is your problem, but it is easily checkable - run alsamixer from the terminal and turn all the outputs down till they are out of the red - although this isn't a real fix, and may not even solve your problem, you might as well give it a shot.....

---

