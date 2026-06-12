---
title: "[SOLVED] Need guidance for Nvidia in Gutsy"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Canew on 2007-11-27
Hi:

I have a Nvidia Geforce FX 5200 card. Yeah, I know, not the newest thing on the block, but it worked fine under Windows until about a year ago when I first put in Edgy. Long story short, some games worked, some didn't, and DVDs were out of synch with the sound.

Now, I've installed Gutsy and DVDs work perfectly (yay!) but I can't get games to work in Wine. I also downloaded the latest version of BZFlag and it does not work well at all. I suspect it's my video drivers, but I don't know for sure, and I'm frankly a little freaked out about breaking something instead of fixing it, so....

1) How can I check to see if I have the latest Nvidia drivers for my card on the system BEFORE I try doing anything?

2) If they are out of date, what is the SAFEST way to install the new ones, set everything up, etc.?

---

### Post by tranquito on 2007-11-27
I used the Restricted Drivers Manager in administration tools to get the Nvidia drivers for my card and its working better now. I heard lotsa games don't work with wine tho.

---

### Post by Canew on 2007-11-27
Well, the manager says the accelerated driver is enabled but "not in use." Do I have to install something? I looked in Synaptic and found three binary X.org drivers. None of them are on my system, but I'm pretty sure I need one of them. Trouble is, they make vague reference to "older" or "newer" Geforce drivers. I'm not sure where mine lies. It's an FX 5200. Is it old enough for the "legacy" driver, or should I get the "new" one?

---

### Post by Canew on 2007-11-28
Sorry to bump this, but I'm really stuck here. Why would the box be checked under "Enabled" in the manager but have it still show the red dot and "Not in use?"

---

### Post by ukripper on 2007-11-28
> **Canew said:**
> Sorry to bump this, but I'm really stuck here. Why would the box be checked under "Enabled" in the manager but have it still show the red dot and "Not in use?"

You have to tick that and make it go green

Something like that in attachment

---

### Post by Canew on 2007-11-28
Yes, but how do you make it go green? The box is checked already, like two of them in the example you showed. Does it have to do with the binaries?

---

### Post by Gildp67 on 2007-11-28
Im new to the Ubuntu world but the one thing I found that made my life easier was installing Envy it totally makes video driver installation easier. I hope it helps

---

### Post by Canew on 2007-11-29
Fixed!

My xorg.conf file was missing, so I couldn't enable the new drivers. File's been replaced, graphics now seem to be humming along normally *knock virtual wood*

---

