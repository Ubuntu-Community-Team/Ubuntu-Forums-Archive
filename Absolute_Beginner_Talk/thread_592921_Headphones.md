---
title: "Headphones?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Ghosts on 2007-10-26
Hey, I just installed Gutsy on my laptop, and for some reason I'm getting sound out of my headphones and speakers at the same time. (after a while of trying to get my headphones to work at all :() How can I get it so that the audio only comes from my headphones?


Also, it says I can't mount my Seagate external drive. any way to fix this? (unrelated lol)

---

### Post by TidusBlade on 2007-10-26
About the headphones, try right clicking the volume control thing in the top right, and then Open Volume Control, then Prefrences, I think you got both headphones and speakers channels on, this might be the problem, so disable one.
About the segagate try using ntfs-3g which can be found in Synaptic ;)
Hope it helps :D

---

### Post by Ghosts on 2007-10-26
I did, if I turn off headphones, everything turns off, if I turn off PCM, they all turn off, if I turn off front, they all turn off.
:(

---

### Post by TidusBlade on 2007-10-26
Then try in the volume Control; File> Change Device, might be something there...

---

### Post by Ghosts on 2007-10-26
tried 'em all

:'(

---

### Post by Dr Small on 2007-10-26
Make sure that the audio port that you are pluggin your headphones into, actually works..
I have had that problem before.

---

### Post by Ghosts on 2007-10-26
It worked when I had windows installed

---

### Post by sweetfishremix on 2007-10-26
I'm having the same problems. My altec lansing speakers wont work when I connect them into the headphone jack. I tryed the shutting off of the master and the pcm thing the sound just keeps comming out of my speakers. Same with the change device. And Also my external hardrive the Maxtor 250gb hardrive wont work as well it says It cannot mount the new volume. Help please T_T

BTW: I AM VERY VERY NEW at this.

---

### Post by Ghosts on 2007-10-26
Same here
D:

---

### Post by ceminino on 2007-10-30
I have the same problem too, what's strange it first worked fine and since a X crash I have this anoying bug.

---

### Post by Lothas on 2007-11-17
I'm trying to do something similar here too. I have both the speakers and headphones connected all the time (also in windows) and both output sound. However, when I'm speaking on skype I usually use only the headphones to reduce background noise.

Any idea on how to switch back and forth (through software) between the headphones and the speakers?

---

### Post by Dr Small on 2007-11-17
> **Lothas said:**
> I'm trying to do something similar here too. I have both the speakers and headphones connected all the time (also in windows) and both output sound. However, when I'm speaking on skype I usually use only the headphones to reduce background noise.

Any idea on how to switch back and forth (through software) between the headphones and the speakers?
Right click on your volume icon and select, "Open Volume Control", go to Switches tab and select "Headphone" ?

---

### Post by Lothas on 2007-11-17
Yes, I found that option but it only turns off my headphones and I'm trying to go the other way around. I'm actually thinking about using that option and connecting the speakers and headphones in the opposite plugs. Yeah, I'm crazy!

---

### Post by Lothas on 2007-11-18
So there's no software, package or workaround out there to add a little box above the "headphones" one so I can disable the speakers instead of the headphones?

BTW, I tried controlling the volume from the konsole but I couldn't separate headphones from speakers.

---

### Post by sweetfishremix on 2007-11-18
My problem is that, The sounds comes out of my laptops speakers, but not the headphone jack. When I go to volume control I see Master and PCM. I altered each one and it just turned the sound off completly and no sound from my headphones. Then I tryed change Device, and I switched from alsa to OSS mixer, and still no results. Can Someone please help me.

---

### Post by Sims2789 on 2007-11-18
> **sweetfishremix said:**
> My problem is that, The sounds comes out of my laptops speakers, but not the headphone jack. When I go to volume control I see Master and PCM. I altered each one and it just turned the sound off completly and no sound from my headphones. Then I tryed change Device, and I switched from alsa to OSS mixer, and still no results. Can Someone please help me.

What computer do you have? It could be computer-specific, especially if it's a laptop.

Did you make sure only the Headphones box is checked in the Switches tab in Volume Control? Also, use whatever ALSA option appears in System -> Preferences .> Sound -> Default Mixer Tracks.

---

### Post by Bruce M. on 2007-11-18
> **Sims2789 said:**
> What computer do you have? It could be computer-specific, especially if it's a laptop.

I have the same problem, and I have a desktop, running Feisty.

Device: 0 Intel 82801BA-ICH2 (Alsa Mixer)
Master <- does nothing
PC Speaker <- does nothing
Headphone <- controls volume
PCM <- controls volume

Device: 1 Analog devices AD1885 (OSS Mixer)
Two options show:
Speaker - <- does nothing
PCM-2 <- controls the sound

Therefore the Volume Control on my pPanel is usless in both cases.
The volume controls on my keyboard don't work either as they control "Master" if using Device 0

> **Sims2789 said:**
> Did you make sure only the Headphones box is checked in the Switches tab in Volume Control? Also, use whatever ALSA option appears in System -> Preferences .> Sound -> Default Mixer Tracks.

After re-reading this I went to System > Preferences > Sound > Default Mixer Tracks and set it to: PCM.  So at least the volume controls on my keyboard work.  Just not with Master Control from the panel.

I'll be watching this thread with interest.
Thanks...

---

### Post by sweetfishremix on 2007-11-20
> **Sims2789 said:**
> What computer do you have? It could be computer-specific, especially if it's a laptop.

Did you make sure only the Headphones box is checked in the Switches tab in Volume Control? Also, use whatever ALSA option appears in System -> Preferences .> Sound -> Default Mixer Tracks.

Im using a Sony Vaio VGN-FZ140E
I tryed it and still no results T_T

---

### Post by jordank on 2007-11-20
> **Lothas said:**
> Yes, I found that option but it only turns off my headphones and I'm trying to go the other way around. I'm actually thinking about using that option and connecting the speakers and headphones in the opposite plugs. Yeah, I'm crazy!

this actually seems like a really good idea.

---

### Post by Lothas on 2007-11-20
Yeah, actually both ideas are feasible so I guessed someone should've already created a little piece of software to do that hardware change... Anyway, if it doesn't exist, I guess I'll go with the hardware solution. Maybe the software solution could be added to Hardy...

---

### Post by Bruce M. on 2007-11-23
> **Lothas said:**
> Yes, I found that option but it only turns off my headphones and I'm trying to go the other way around. I'm actually thinking about using that option and connecting the speakers and headphones in the opposite plugs. Yeah, I'm crazy!

> **jordank said:**
> this actually seems like a really good idea.

My motherboard has:  
[LIST]
[*]Line In,
[*]Line Out
[*]Mic.
[/LIST]

Guess I'm between a rock and a hard place.  :cry:

---

### Post by Lothas on 2007-12-09
Any progress on switching speakers off instead of headphones?

---

### Post by smhuey on 2007-12-19
I guess I am having similar issues, although I really could care less at this moment because I am off of vista :).  Whats funny is that I am having the same issues with my fz140e. I have already played around with the mixers and the volumes, but I am not getting any audio through audio jack port.

---

### Post by starryeyedboy on 2007-12-26
hi guys - i'm having a similar problem.

when i plug in my headphones, my speakers don't mute. so i get sound from headphones n speakers.

i'm using a lenovo n100 - running on gutsy. its not a big issue - but it would be good to have it fixed =D since everything else is perfect at the moment. even the broadcom wireless worked.

any ideas on fixing it up? i can't find the headphone option in my volume properties thing. tried clicking each one on n off without results - the best i could do was turn both off.. which isn't what i am looking for..

---

### Post by (((X))) on 2007-12-28
Plug earphones in, mute volume, now unmute it, now the sound should come only out of yout earphones. I also modifyed my mixer.

---

### Post by andechs on 2007-12-28
> **(((X))) said:**
> Plug earphones in, mute volume, now unmute it, now the sound should come only out of yout earphones. I also modifyed my mixer.

I got mine to work just by muting the Front volume with *HDA intel (alsa mixer)* device when I want to listen through my headphones. Any ideas on how to get the machine to recognize when I plug/unplug my headphones and mute/unmute accordingly?

---

