---
title: "Sound Ahhhhh"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by linux_dummy on 2006-08-02
Hiya, I am having trouble with the sound on my PC, I am running Ubuntu 606. I am fine with Windows XP but do not have a clue about Linux, I have been looking through various forums for days, and I have tried MANY things to get my sound working on my PC and it just isn't working, I have downloaded Realplayer 10.0 or linux and that now (after some playing around) opens up and when I select a file to play, it looks like it is playing it but I can hear no sound.

However when I receive an email it beeps to let me know I have an unopened email.

I think I need to start at the beginning, and please make it easy 4 me to follow Iam a TOTAL dummy when it comes to linux.

Thanks for any help

Linux_Dummy.

---

### Post by ironfistchamp on 2006-08-02
Do you know what hardware you have. I mean for audio output. Could be you need extra drivers. I don't have much experience here because it has always worked for me but it might help someone else on here fix this for you.

---

### Post by Sweet Spot on 2006-08-02
Also, which desktop environment are you using ? KDE or Gnome ? I know that in KDE, there's an app in multimedia called Kmix which essentially is a master/internal volume control source. There's a similarly named app in Gnome(gmix maybe?) located in the same place. Open that app and play w/master volume and PCM volume. I set both master and PCM to about %80 and turn my physical volume knob on my speakers all the way up, and control the volume with the media player volume. 

Regards, 
Doug

---

### Post by xpod on 2006-08-02
I had that problem yesterday but a simple couple of lines of code i was given solved it.
You can see the "code" if you go look in the "automatix" sub-forum further down the forum index.....under automatix V synaptic.
Plus theres another thread under that with the same sound issues.

They might help

edit.Sorry,that was AFTER i downloaded automatix my sound went

---

### Post by linux_dummy on 2006-08-03
Hiya, I am used to using Windows, where I could just go to device manager etc, so I have no idea to find out what my hardware is and wether I am using gnome etc!! In the device manager under sound it says "SIS S17012".

I am OK using the terminals, but it gets a bit confusing at times.

Thanks for your replys.

---

### Post by linux_dummy on 2006-08-03
P.S. at the moment I am using Real Player to play music.

Thanks.

---

### Post by ironfistchamp on 2006-08-03
Right are you dual booting? If you still ahve windows you could go in there and find out. I have found that Linux doesn't report my hardware all that well. Everything comes back as <unknown device> although everything works.

To find out if you have Gnome or KDE hmm. When you first ever used Ubuntu did it have two bars (one at the top and one at the bottom) or did it have just the one big one at the bottom (a bit like windows).

---

### Post by tommcd on 2006-08-03
In gnome you would run: alsamixer  to get the master volume control.

---

### Post by tommcd on 2006-08-03
See this thread for sound help:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound)

Hope this helps!

---

### Post by ironfistchamp on 2006-08-03
Great find Tommcd looks like that may help me when I run into probs.

---

