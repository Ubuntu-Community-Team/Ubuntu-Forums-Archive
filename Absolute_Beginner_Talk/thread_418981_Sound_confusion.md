---
title: "Sound confusion"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by censored77 on 2007-04-22
I have two sound devices on my system. An internal soundcard that I've never really used, and an Alesis I/O2 USB audio device that I use for some basic recording in XP.

Ubuntu is happy enough playing through the USB device, although it's not officially recognised. Except for any sounds coming from Firefox, or login/logout sounds... any ideas why?

If I switch the settings to use the soundcard, I get exactly the same thing - audio from anything  but Firefox and the OS itself.

---

### Post by leibowitz on 2007-04-22
There's a lot of different profile for sound applications. 

Gnome use his own sound deamon (in fact, it was from another project but that's not the problem). It's called ESD. 

Now totem use gstreamer, and gstreamer use alsa. 

And etc. 

Note: this is not totally accurate.

Anyway, what I mean is you need to configure on a per application basis for your audio setup. And that's sometime true with only one sound card aswell. Because many applications used OSS, and they are almost all switched to alsa now.

So please report here what application you want to try with your USB sound device, and maybe we can help you then.

---

### Post by censored77 on 2007-04-24
It seems everything uses the internal sound card except for Firefox and anything played by it's internal plugins, plus system sounds like the logon/logoff tunes.

So Rhythmbox plays though internal, as does Movie Player. Audacity plays via internal and crashes if you try to use the USB device. I'd like everything to use the internal card, since at the moment the external device is for recording that I can't do in Linux anyway...

---

### Post by deadgobby on 2007-04-24
Try disable the on board sound card in the BIOS and see if all the sound will default to your usb device. 
Gobby

---

### Post by leibowitz on 2007-04-24
You have to go to the System menu, Preferences, Sound.

And see the "Default sound card" on one of the tab. My version of Ubuntu (6.06) has this option on the bottom of the first tab called "Sound". But it may differ with newer versions.

Anyway, try selecting your internal sound card in it. It will makes the "bip" sound and alike played by this card. I don't know precisely about Firefox, but it should change aswell.

---

### Post by censored77 on 2007-04-24
It seems to be different whenever I go it... looks related to the last option, Default Mixer Tracks. The other day it had the soundcard but not it's only got the USB device.

I'll try unplugging the USB device and only plug it in for my work in XP, which isn't ideal but then I need to switch speakers anyway...

---

### Post by leibowitz on 2007-04-24
Post any revelant information you have. A screenshot of this interface would be particulary appreciated. 

Note that the Default Mixer track is only useful for handling sound from the keyboard (with special keys). I think it's writed somewhere on the sound configuration interface.

---

### Post by censored77 on 2007-04-24
OK, well I'll try with the USB device unplugged which will save a lot of hassle, and come back if it doesn't work!

Thanks for your help...

---

