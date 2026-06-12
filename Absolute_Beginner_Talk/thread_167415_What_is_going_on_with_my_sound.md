---
title: "What is going on with my sound?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Insane on 2006-04-28
I have an Audigy LS soundcard, and it works perfectly in Windows (and used to work in other linux distro's) but now that i ahve switched to Ubuntu I get no audio whatsoever. I am clueless as to what is going on. I went to synaptic and installed everything to do with "audigy" and the alsa sound server seems to be working.

According to "Sound Preferences" I am using the CA0106 card/driver.

Well, my speakers are on and my volume on the sound thing is set to the highest level.

I am using Dapper Drake alpha.

---

### Post by jazzmuzik on 2006-04-28
Man, there are so many different Creative sound boards they are hard to remember... Anyway, I *think* it was the Audigy LS board that I bought for use with Linux (fedora) a couple of years ago and was disappointed to find that it wouldn't work. That may not be the case today though!! I was bummed and went back and bought a cheap SB card that had the emu10k1 chip on it. That one works great with Linux. Don't be discouraged though, I may have my boards confused, so it may work. See what others have to say on this issue or do a Google search to find out more.

BTW, Dapper is now in beta 2.

Related links:
[LIST]
[*][http://www.linuxcompatible.org/thread28166-1.html](http://www.linuxcompatible.org/thread28166-1.html)
[*][http://www.zamazal.org/linux/audigy.html](http://www.zamazal.org/linux/audigy.html)
[/LIST]

---

### Post by louis_nichols on 2006-04-28
There are many things that could cause you to not have sound.

For starters, if your user isn't included in the audio group (the easiest way to do this is under "users and groups"/user_name/advanced - check the option "use audio devices"), it won't have sound (you can test if this is the case by checking if root has sound). Then, you need to set alsa both for output and sink under multimedia systems selector. Then  you need to configure all multimedia apps to use alsa for output.

---

### Post by Insane on 2006-04-28
But why wont my sound work in ubuntu yet it works with all the other distro's I have used. i want to cry. Why am I always the one with the problems. :'(

---

### Post by jazzmuzik on 2006-04-28
Don't get discouraged. If 99% of Ubuntu is working, keep working on the last 1%. Let's see of others have any solutions:

This thread show people using Audigy LS successfully:
[http://ubuntuforums.org/showthread.php?t=88639&page=5&highlight=audigy+ls](http://ubuntuforums.org/showthread.php?t=88639&page=5&highlight=audigy+ls)

According to this, Audigy LS does work with the alsa sound system:
[http://alsa.opensrc.org/Alsa+Preferred+Soundcards](http://alsa.opensrc.org/Alsa+Preferred+Soundcards)

So I would say that card DOES work with Ubuntu. It's just a matter of getting it set up. 

What does System, Preferences, Sound show?

What about System, Preferences, Multimedia Systems Selector?

Did you double click on the little speaker icon in the toolbar to see if the speaker is muted?

---

