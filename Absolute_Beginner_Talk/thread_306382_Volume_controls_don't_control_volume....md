---
title: "Volume controls don't control volume..."
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by wrybread on 2006-11-24
I have a second soundcard on my laptop, and apparently most of my applications aren't using it on my new Ubuntu 6.10 install. I go to System --> Preferences --> Sound and set everything to that soundcard, confirm that it's working with test tones, and all seems well. But, for example, Totem Movie Player is mute, and has no apparent place in it's preferences to fix it.

Another clue is that XMMS plays sound after I told it to use the USB audio device in it's preferences, but it's volume slider has no effect on the volume. 

I set the Master Volume that's docked at the top right of the panel to control the USB audio card and now I can control it with that, but a) that's inconvenient, b) it still doesn't solve the problem of no sound in most apps, and c) I'm curious what's causing the problem.

Anyone have a clue about this?

---

### Post by CaveRat on 2006-11-24
Yup! Got the same here. Basically I think what has happened is I have turned the volume control over to the external audio alsa mixer. I don't mind because I can better control the sound output to my home receiver. By fine tuning the PCM and Master volume controls, I get good sound clarity throughout my surround system.

---

### Post by wrybread on 2006-11-25
Interesting. Yeah the built-in soundcard in my laptop, which is broken, is an  OSS card, and the USB card is an Alsa. Truth be told I have no idea what that means, but I have a feeling these applications are trying to control an OSS card, and therefore missing my Alsa card. 

Wondering if there's some way to get these apps to control an Alsa card?

Or if I'm barking up the wrong tree?

---

### Post by Voxxi on 2006-11-25
In Preferences -> Sound, have you got ALL the bars turned up full? By default not all the bars are visible. You need to go to Edit -> Preferences and tick all the ones you want visible. Thats what happened with my sound card. ;)

---

### Post by crispy_420 on 2006-11-25
Quick thought...

Can you just disable the on board sound card in your bios. That seemed to solve my desktop's issues with audio. Just an idea. If you aren't using it, what harm could it do.

---

### Post by wrybread on 2006-11-25
Alright, I admit it, I'm an idiot. I set my soundcard as the main card in the Preferences --> Sound --> Devices folder tab, but didn't notice the "default soundcard" parameter at the bottom of the Preferences --> Sound --> Sounds folder tab. Setting my soundcard as the default soundcard there seems to have fixed all.

Thanks for all the clues.

---

