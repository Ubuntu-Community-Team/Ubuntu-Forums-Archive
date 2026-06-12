---
title: "First time in Ubuntu- Sound Problems!"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Skittle on 2007-11-09
This is my first install of Ubuntu, and I absolutely love it!
One thing I can't get right though, is the sound. I can't get sound working for the life of me. Yes, my speakers are plugged in (to the power and computer) and they are turned up, and on. And the volume control is up to 80%. 
I've installed VLC media player already, but I just can't get sound to play at all. Any help?

---

### Post by Shinbu-Otaku on 2007-11-09
Welcome to Ubuntu!

Now, what kind of speakers are you using? Does they come with a Windows installation disc? Are your speakers plug & play?

I ask because:

1) If it has a windows install disc, it may not have a linux driver yet, meaning they wont work until a driver is made (i have a webcam im trying to sort out, it has a windows driver but no linux equivilant, which is annoying...) 

2) If they are plug & play they should theoretically work, but your set-up may prevent this (i doubt it though)

and 3) Some makes are less likely to have drivers for linux (but once again, this is only a matter of time)

---

### Post by Skittle on 2007-11-09
The speakers are Altec Lansing ... I forget exactly which set, my father gave them to me when he got a new sound system. It's a set of two small speakers, and a subwoofer if that helps at all. 
If there was a disc with drivers on it, my dad lost it long ago :P

---

### Post by Trebaruna on 2007-11-09
@Shinbu: I think you mean sound card, as the speakers just accept electrical signals from the sound card. Speakers are always plug and play.

What *is* important, though, is to figure out what soundcard you have.
If you right-click on the volume icon in the system tray and click preferences it should tell you what card it is using, with what drivers.

Alternately, if you use the terminal to type "lspci | grep audio" without the quotes, it should say what sound card you have.
lspci means list stuff on the PCI bus, and grep allows you to only display stuff that matches a string (audio in this case).

---

### Post by Skittle on 2007-11-09
The sound card is onboard. 
Wow.
That just hit me.
I need to install the drivers from the motherboard CD.
God I feel like such an idiot. Will the CD work on Ubuntu? I've only ever used it on windows.
(sound card by the way is called C-Media Electronics CMI9739)

---

### Post by Trebaruna on 2007-11-09
Most likely no, the CD will not work.

However, the good news is that the generic "intel-8x0" can power this chip, and as far as I know it should be included with Ubuntu.
Did you check to see what sound card/driver Ubuntu is actually seeing? Like I said, right-click on the volume icon and select preferences.

---

### Post by Skittle on 2007-11-09
Yeah, the CD won't work... just popped it in.
Anyway, I checked to see what sound card it's actually seeing, and it said the one I specified with "(oss mixer)" at the end, and another option, which is SiS SI7012 (Alsa Mixer).

---

### Post by Trebaruna on 2007-11-09
Well, I'm not much of an expert myself, but I'll try and help some more ;)

Please try and select the ALSA driver. Does that work?
In Volume Control, under File, you can change the device you're arranging volume for. Try playing with that a bit.

---

### Post by Shinbu-Otaku on 2007-11-09
> **Trebaruna said:**
> @Shinbu: I think you mean sound card, as the speakers just accept electrical signals from the sound card. Speakers are always plug and play.

You're right, my mistake :( thought he meant the sound card lol

You *may* be able to find linux drivers on the company site for your sound card, but i can't quite tell why linux didnt pick it up, practically all onboard hardware is supported 'out-of-the-box'...odd....

---

### Post by ushills on 2007-11-09
Check the volume controls for some reason the control for PCM volume on my install was turned down low when I did a fresh install, you need to ensure that this slider is not on zero.

---

### Post by Skittle on 2007-11-09
Thank you :D
I selected the ALSA driver, and no sound still. I changed the device and played with it for a bit...  a lot, actually... and still nothing.

I checked the PCM sliders just now and they're turned almost all the way up.

---

### Post by Trebaruna on 2007-11-09
I've no experience with that chip, so I'm starting to run out of ideas, but what you could do is try and enable additional mixer things in the volume control: one of them might be muted/low.
In volume control, click edit then preferences.
I'm afraid that's all I can think of...

---

### Post by Skittle on 2007-11-09
Kay, I'll play around with that for a little while. Thank you for all of your help!

EDIT: I've played with pretty much everything that can be done... so as a last resort I'm going to boot to windows real quick and see if I can't gather some information... I know for a fact the sound works in windows. 
Soooooo incredibly tired of windows.

---

### Post by philinux on 2007-11-09
This is why no sound.

[http://edseek.com/archives/2004/03/03/c-media-electronics-cmi9739-mixer-pcm-no-volume/](http://edseek.com/archives/2004/03/03/c-media-electronics-cmi9739-mixer-pcm-no-volume/)

---

### Post by Hayden on 2007-11-09
I don't know if this will help, but you can set your default soundcard in the terminal.

```
sudo asoundconf list

Names of available sound cards:
Live
V8237

sudo asoundconf set-default-card Live
```

In this example, I set the default to "Live". I had to do this even when I had only integrated sound.

---

