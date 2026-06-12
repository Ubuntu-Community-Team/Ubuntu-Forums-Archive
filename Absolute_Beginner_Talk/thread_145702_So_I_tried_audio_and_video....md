---
title: "So I tried audio and video..."
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by cryptidan on 2006-03-16
to no avail...I was recommended linux, so i give it a try, besides the fact that i dont want to drop no loot on XP
I do two things on the computer.  Play and download music (mostly Grateful Dead, so imagine the size of my collection), and play a couple games (These are all set)

I have used BitTorrent, Azureus, Bitlord, uTorrent, whatever, i'm familiar with them all.  I normally use Creative Media Player for listening, but also familiar with winamp, and i'm grateful to see XMMS...

So this is no problem.

The problem is my soundcard.  It tells me that another application is using the soundcard, how can this be solved?
I have combed these forums from top to bottom, and tried it all...This is my last ditch attempt (before I try something else, cuz I STILL ain't buying XP)
This is my most recent try. Here ya go, in all its glory:

root@oldmine:/tmp# modinfo snd-ens1371
filename: /lib/modules/2.6.12-10-386/kernel/sound/pci/snd-ens1371.ko
author: Jaroslav Kysela <perex@suse.cz>, Thomas Sailer <sailer@ife.ee.et hz.ch>
license: GPL
description: Ensoniq/Creative AudioPCI ES1371+
vermagic: 2.6.12-10-386 386 gcc-3.4
depends: snd-pcm,snd-rawmidi,snd,gameport,snd-ac97-codec
alias: pci:v00001274d00001371sv*sd*bc*sc*i*
alias: pci:v00001274d00005880sv*sd*bc*sc*i*
alias: pci:v00001102d00008938sv*sd*bc*sc*i*
srcversion: D3D8CC5AD67BB5BCEE48E2D
parm: joystick_port:Joystick port address. (array of int)
parm: enable:Enable Ensoniq AudioPCI soundcard. (array of bool)
parm: id:ID string for Ensoniq AudioPCI soundcard. (array of charp)
parm: index:Index value for Ensoniq AudioPCI soundcard. (array of int)
root@oldmine:/tmp# /etc/modprobe.d/sound
bash: /etc/modprobe.d/sound: No such file or directory
root@oldmine:/tmp# cd /usr/share/sounds
root@oldmine:/usr/share/sounds# aplay xxx.wav
ALSA lib confmisc.c:560snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479_snd_config_evaluate) function snd_func_card_driver return ed error: No such file or directory
ALSA lib confmisc.c:392snd_func_concat) error evaluating strings
ALSA lib conf.c:3479_snd_config_evaluate) function snd_func_concat returned er ror: No such file or directory
ALSA lib confmisc.c:955snd_func_refer) error evaluating name
ALSA lib conf.c:3479_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3948snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2090snd_pcm_open_noupdate) Unknown PCM default
aplay: main:533: audio open error: No such file or directory
root@oldmine:/usr/share/sounds#
root@oldmine:/usr/share/sounds# sudo fuser -v -m /dev/dsp
/dev/dsp: No such file or directory
root@oldmine:/usr/share/sounds# /etc/hotplug/blacklist
bash: /etc/hotplug/blacklist: Permission denied
root@oldmine:/usr/share/sounds# sudo modprobe es1371
root@oldmine:/usr/share/sounds# [/etc/modules] add 'ens1371'
bash: [/etc/modules]: No such file or directory
root@oldmine:/usr/share/sounds# [esd]
bash: [esd]: command not found
root@oldmine:/usr/share/sounds# /etc/asound.conf
bash: /etc/asound.conf: No such file or directory
root@oldmine:/usr/share/sounds# cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
root@oldmine:/usr/share/sounds# ls -l /dev | grep dsp

as you can see, I have *no* idea of what I am doing....

---

### Post by ronmarley1 on 2006-03-16
cryptidan,
If anything, I've gotta try and help just because of your choice in music.  ;)
Did you try going into System -->Preferences -->Multimedia Systems Selector and trying some of the different outputs?  Choose the different selections and then try the "Test" button.  Give that a try and let me know what happens...
When in doubt, twirl!

---

### Post by cryptidan on 2006-03-16
Excellent! Thats what I like to see!

Ok, yeah I tried that a bit back and found that video seems fine, gives me a test screen, so thats good..

But with every try on Multimedia, etc...ALSA, OSS, ESD, and even custom give me the "failed to construct test pipeline for (said attempt)"

---

### Post by ronmarley1 on 2006-03-16
Did you see this area? [http://www.ubuntuforums.org/forumdisplay.php?f=114](http://www.ubuntuforums.org/forumdisplay.php?f=114).  I'm not sure there's an answer there for you...  I'll keep looking

Maybe this: [http://www.ubuntuforums.org/showthread.php?t=114955&highlight=Ensoniq%2FCreative+AudioPCI](http://www.ubuntuforums.org/showthread.php?t=114955&highlight=Ensoniq%2FCreative+AudioPCI)

---

### Post by cryptidan on 2006-03-16
Yeah, I pretty much went thru all that, too...

---

### Post by Sandlst on 2006-03-16
quick question: have you tried running xmms from a terminal?  If not try it under (Applications/Accessories/Terminal)```
xmms
```  Ive found trying to start any games from the menu results in the same error you are getting for me on this machine-if it works from the terminal, disable the 'click' noise under (System/Prefences/Sounds/Sound Events) and Remove the file to play on the "Click on command button" line.  Hope this helps!

---

### Post by cryptidan on 2006-03-16
Yes, that works, but no access to actual music, because it says that  /dev/dsp is missing?

---

### Post by Sandlst on 2006-03-16
Have you tried to mess around with the Output Plugins by right clicking on xmms, going to options/Prefences and trying to change to, and configure each Output Plugin?  Very time-consuming and frustrating I know-but I had to do this with mplayer (via hit/miss :P) so maybe it will work for you? /dev/dsp is used by the OSS plugin I believe....

---

