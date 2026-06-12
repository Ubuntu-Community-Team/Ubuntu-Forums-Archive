---
title: "Alsa-control"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by DarkIce101 on 2006-07-21
Hey.  When I play a file in MPlayer the error "alsa-control: unable to find simple control 'PCM',0" pops up repeatedly.  I have searched Google and this forum and have not found a solution yet.  I have disabled the Onboard soundcard but that did not help.  Im using a Soundblaster Live! 24-bit.

Thanks

---

### Post by DarkIce101 on 2006-07-21
anybody?

---

### Post by deadgobby on 2006-07-21
Just kinda funny question. Did you install mplayer-skins in synaptic? When after I upgraded from B to D. ( What happen to C?) I could not get Mplayer working right till I install the Mplayer Skins.
GObby

---

### Post by DarkIce101 on 2006-07-21
No I didn't.  I will try, although I don't think that the skins have anything to do with the error im getting.

Thanks

---

### Post by deadgobby on 2006-07-21
Some times in the world, all is wrong is just a loose screw. And there is lots of them.:lol:

---

### Post by patrick295767 on 2006-07-21
> **DarkIce101 said:**
> Hey.  When I play a file in MPlayer the error "alsa-control: unable to find simple control 'PCM',0" pops up repeatedly.  I have searched Google and this forum and have not found a solution yet.  I have disabled the Onboard soundcard but that did not help.  Im using a Soundblaster Live! 24-bit.

Thanks

Normally the fresh installatino is the one for xmms

sudo alsamixer
then 
to get sound all right.
   
   
=====
Did you try : 
OSS Driver libOSS.so

---

### Post by DarkIce101 on 2006-07-21
I did Sudo Alsamixer, but that only presents you with the volume controls.  Unless im missing something.

---

### Post by DarkIce101 on 2006-07-22
Bump

---

### Post by buntumaddy on 2006-08-09
I'm having the exact same problem with MPlayer. In fact, that's the only gripe I have with my Ubuntu installation at the moment. I've had everything else working perfectly, including xgl/compiz.

Whenever I play anything with mplayer, both audio and video play fine but this error box keeps poping up (probably for every frame) and thus dosen't let the video play properly. Have messed with almost all settings (mixer and volume control) but in vain. This error message does not pop up if I select OSS or ESD audio output, but in that case, video lags the audio by about 1.5 seconds (just a rough guess). Music plays fine in Rhuthmbox. So I know my sound card is working good. Just Mplayer needs some fix.

Somebody who can suggest the fix?

---

### Post by p!u$ on 2006-08-28
buntumaddy
It work fine for me with ESD thx!

---

### Post by wilberfan on 2007-02-23
"OSS" worked for me (in openSUSE 10.2!)...

---

### Post by thinkbox on 2007-06-08
The problem is that MPlayer can't get a handle on the proper mixing device. Go into your preferences, and either choose to use OSS drivers or try the "Software Mixer". I am confident that this will resolve your issues.

---

### Post by ramjet_1953 on 2007-06-08
Give this a try.

If it isn't already installed, install [COLOR="Blue"]alsa-oss[/COLOR] using Synaptic, or apt-get install.

start mplayer with the command [COLOR="Red"]aoss gmplayer[/COLOR]

Just a thought, but it's worth a try, as there are problems, as you probably know, between OSS and ALSA.

Regards,
Roger

---

