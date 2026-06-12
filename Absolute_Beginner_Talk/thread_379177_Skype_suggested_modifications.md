---
title: "Skype suggested modifications?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-03-08
Hi everyone, I've been having a little trouble with skype. I get an echo delay whenever I speak to people, very offputting!
The people at skype have made a couple of suggestions, the first ones made no difference and now they're suggesting I make modifications to alsa.
I'm, 1; concerned about changing things that are working, ie ALL my sound stuff works just great except skype, and 2; I don't really know how to make such changes.

This is what is suggested - > In order for Linux to recognize and use your soundcard, you have to load the appropriate driver. As of the 2.6 version of the kernel, that means enabling the ALSA (Advanced Linux Sound Architecture) driver for you card. Take a look at the ALSA Soundcard Matrix to determine which driver you are supposed to use for your speciffic card.

Now, you will have to modify your /etc/modules.conf or /etc/modules.d/alsa (check your distribution for details on the correct way to load and configure modules) and add the following:
Code:

# This sets up the ALSA and OSS portion
alias char-major-116 snd
alias char-major-14 soundcore

# Replace "driver" with the driver for you soundcard
alias snd-card-0 snd-driver
alias sound-slot-0 snd-card-0

# Configure the OSS emulation layer
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

# If you have more than 1 card, set this number to the correct value
options snd cards_limit=1
options snd-pcm-oss nonblock_open=1

Note that a lot of this configuration is dedicated to something called OSS (Open Sound System) emulation. This mimics the behaviour of the old Linux sound system so as to be backward compatible with older software that does not yet support the new sound system. One such piece of software is Skype - so it is important that it is running and configured correctly.

Now, it is time to load the drivers. How you do that depends on your distribution - you may have an /etc/init.d/alsa or similar script that will do it for you. If you are unable to figure it out, a reboot will do it


One of the difficulties here is that according to my owners manual I've got a Sigmatel STAC9220 audio card and I don't see anything like that in any of the lists I've managed to find in the ALSA files. Or a driver for that matter. I assumed it was handled by default - a standard setup.
My questions is; Do my drivers need altering? or is there another method for this? I have looked thru the forums for this over the last few weeks. I've tried a few things but of course without success.:confused: 
Any advice is most welcome!:) 
especially simple advice.
thanks.

---

### Post by [S|G] on 2007-03-08
Are you using an old skype release? The latest version supports alsa directly with no need for OSS emulation. You could try to check that on skype's website and try the latest version.

---

### Post by Bwosc on 2007-03-08
Have you tried any other VOIP apart from Skype? To me it seems that the app is having some difficulties.

---

### Post by 3rdalbum on 2007-03-08
Don't fiddle with ALSA - if it breaks, you lose all sound on your computer.

Echo on Skype is not uncommon. It can sometimes be caused by internet traffic, sometimes it happens randomly. Do you get the same problems when talking on the Party Line in Gizmo?

---

### Post by carloslosgrande on 2007-03-08
Hi, I have the latest version of skype. I use it because my brother does so I can talk to him in Aust. The other voip's in synaptic don't work for me. ie Ekiga and Wengo. My brother has a Mac so I don't know how compatible his system is with linux stuff.

I really wasn't keen on fiddling with alsa.

It doesn't seem to happen randomly, it happens every time. I only have the one contact so I don't know if the problem always happens with others.

I have no idea what > Party Line in Gizmois?:confused: 

But hey, thanks for your answers.

I just googled gizmo and now I'm downloading.

---

