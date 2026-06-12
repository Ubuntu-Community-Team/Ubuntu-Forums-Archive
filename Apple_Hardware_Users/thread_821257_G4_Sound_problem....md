---
title: "G4 Sound problem..."
date: 2008-06-07
forum: Apple Hardware Users
---

### Post by irwing on 2008-06-07
I'm having some audio problems. Sound is working fine over the 5-10 secs. after some app. is opened. I made all updates... Anybody could help me? There's a solution?

kernel:2.6.24-18-powerpc
processor	: 0
cpu		: 7450, altivec supported
clock		: 733.333331MHz
revision	: 0.0 (pvr 8000 0200)
bogomips	: 66.30
timebase	: 33217716
platform	: PowerMac
machine		: PowerMac3,5
motherboard	: PowerMac3,5 MacRISC2 MacRISC Power Macintosh
detected as	: 69 (PowerMac G4 Silver)
pmac flags	: 00000010
L2 cache	: 256K unified
pmac-generation	: NewWorld
audio           : PowerPc Tumble

---

### Post by irwing on 2008-06-07
cat /proc/asound/cards
 0 [Tumbler        ]: PMac Tumbler - PowerMac Tumbler
                      PowerMac Tumbler (Dev 21) Sub-frame 0

---

### Post by stream303 on 2008-06-07
Frustrating to have it work for a few seconds and then stop!

I'm not into sound so much, but would try some things to narrow it down...

Which version of Ubuntu are you running?

Have you tried running Alsamixer in a terminal and seeing if anything is muted?  You can mute/unmute with the "m" key, or balance it out with the "b" key.  I've seen some weird interactions with the gui sliders, and have had to rely on alsamixer at times.

Have you tried going into the sound preferences, and changing from say "auto detect" and forcing "Alsa"?

Just some things I'd try since I'm not a sound expert. :)

---

### Post by irwing on 2008-06-07
stream

i'm using hardy... 

sometimes, when testing sound in "Sound Preferences" i get this message in any of the devices: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by avtolle on 2008-06-07
I get the same message when I do that, running a G4 Cube (actually, two of them). I've concluded that for this purpose, the default sound card is not detected (as is shown by the error message in the boot up "no splash" I'm using on one of them). Thus, I've no system sounds at all (log-in, error, etc.), although I've configured Quod Libet, et al, to use Pulse Audio, and have no problems with sound playback whether streaming audio or from CDs, etc. BTW, VLC doesn't give me any sound, either, just "white noise" when running it with the Pulse Audio plug in enabled, which is more than I get with any other audio plug in enabled. I've resigned myself to no system sounds, been that way since 7.04, although I did get the system sounds a short while under 7.10 after installing Pulse Audio and all the tools. Upgrading to 8.04 killed that.

Checked modules in the appropriate places, and snd_powermac or whatever it's called appears there. I've come to the conclusion that my problem lies with no detection/loading of the default sound card, listed as the speakers, which may also be related to the Error: unidentified powerbook message on bootup, which looks for PMU 12, as I recall. 

All this reading just to tell you I've no idea how to help you. Sorry, just needed to get it out there, I guess. :-)
'

---

### Post by [Rolamoto] on 2008-06-10
I'm having the same problem on my G4 "Quicksilver"

---

### Post by oswaldkelso on 2008-06-10
I have noticed that several linux distros fail with sound on these towers by default. There is only one option "powermac tumbler" afaik. The good news is sound does work! You can run alsaconfig as root or alsamixer to adjust sound on Debian based systems. Even then alsactl store (I think) to store your setting does not always work, there seems to be a little voodoo going on regards these cards.

Unplug any usb devices that could be configured for sound. I have had my usb mic picked up as the sound card rather than powermac tumbler. It has no output!


Plug in some headphones as some times the output is working but sent to the phone socket and you can't hear it.


I'll boot into hardy and look at my sound settings tomorrow if anyones still having problems but don't have time atm.

---

