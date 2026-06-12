---
title: "[SOLVED] Need Sound Help"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by comradelurcher on 2008-03-11
Thanks for the help on previous occasions, here's a new one (to me anyway)
Installed Ubuntu and sound effects and music played brilliantly, but on restart, sound wise all I get now is nothing, can anyone give me a clue?   Please bear in mind I'm a noobie and a silver surfer (not alot going for me) and if things have to be posted please tell me how to do it. Ta
p.s no answers in previous posts help,twice i followed 'advice' and it resulted in having to re-install

---

### Post by DamonChyld on 2008-03-11
Hmm, some more info on the situation, or better yet making a new post on your first one, would help us have an idea of what you might have going on.

---

### Post by comradelurcher on 2008-03-11
Tell me how and what to do, and I'll do it.

---

### Post by DamonChyld on 2008-03-11
When you right click > open volume control the speaker icon on the upper right of your top panel is everything turned up/not muted under playback? If you select file > change device what do you have listed?

---

### Post by comradelurcher on 2008-03-11
Everything is turned up.
file>change device, list are :-
0. cordless usb phone (Alsa mixer)
1. NVidia NForce2 (Alsa mixer)
2. USB Mixer (OSS mixer)

---

### Post by DamonChyld on 2008-03-11
Type sudo lshw in a terminal (applications>accessories) and look for *-multimedia (somewhere around the middle).
What does it list there?

---

### Post by comradelurcher on 2008-03-11
*-multimedia
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 mod

---

### Post by comradelurcher on 2008-03-11
ule=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master

Need more??

---

### Post by DamonChyld on 2008-03-11
Try typing gstreamer-properties in terminal and setting all audio properties to alsa and then run alsamixer (in terminal) and mute the IEC958 Capture Monitor.

---

### Post by comradelurcher on 2008-03-11
Ah My Man ....To fast  speak slowly as if to a noobie which I am

---

### Post by comradelurcher on 2008-03-11
Done all up to run alsamixer interminal and then get
alsamixer: function snd_mixer_load failed: Invalid argument

---

### Post by comradelurcher on 2008-03-11
typing gstreamer-properties in terminal, I also get.........
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

---

### Post by DamonChyld on 2008-03-11
I am pretty fresh on Ubuntu too, from 15yrs on windows... don't worry, it'll come faster than you think ;)

Go into Symantic (System, administration, Synaptic Package Manager) and search for alsamixergui

---

### Post by DamonChyld on 2008-03-11
On the gstreamer-properties, did you get that before or after you exited out of the gui (graphical user interface, what you see if it's not code ;))

---

### Post by comradelurcher on 2008-03-11
with my limited knowledge, it seems that it is not installed

---

### Post by comradelurcher on 2008-03-11
On the gstreamer-properties, before I think?

---

### Post by DamonChyld on 2008-03-11
The alsamixer is not installed, you need to get that from synaptic (click it and select install after you pull it up)
The gstreamer-properties should be installed. I get errors similar to yours after exiting the gui - I think that it's trying to pull up non-installed plugins for other devices.

---

### Post by comradelurcher on 2008-03-11
Do I download alsamixergui???

---

### Post by DamonChyld on 2008-03-11
But you were able to change over to asla under audio?
Yes, install alsamixergui

---

### Post by comradelurcher on 2008-03-11
Sorry DamonChyld, I've lost it, downloaded alsamixergui, what do I do now?

---

### Post by DamonChyld on 2008-03-11
Go into a terminal and type alsamixer then mute the IEC958 Capture Monitor. Also under applications>sound&video you now have advanced audio properties to play around with (alsamixergui)

---

### Post by comradelurcher on 2008-03-11
But you were able to change over to asla under audio? Yes it already was!!!

---

### Post by comradelurcher on 2008-03-11
Go into a terminal and type alsamixer then mute the IEC958 Capture Monitor
When I type alsamixer I get.....
alsamixer: function snd_mixer_load failed: Invalid argument

---

### Post by comradelurcher on 2008-03-11
> **comradelurcher said:**
> Go into a terminal and type alsamixer then mute the IEC958 Capture Monitor
When I type alsamixer I get.....
alsamixer: function snd_mixer_load failed: Invalid argument
ALSO same in Applications>sound& video>alsamixer

---

### Post by comradelurcher on 2008-03-11
Not like Windows then, quick restart and everything works???

---

### Post by DamonChyld on 2008-03-11
Hmm.. ok go into synaptic and search for alsa. It should pull up alsamixergui, alsa-utils, and gnome-alsamixer. Uninstall and reinstall the first two (3rd is probably not installed) and give your sound a try

---

### Post by comradelurcher on 2008-03-11
> **DamonChyld said:**
> Hmm.. ok go into synaptic and search for alsa. It should pull up alsamixergui, alsa-utils, and gnome-alsamixer. Uninstall and reinstall the first two (3rd is probably not installed) and give your sound a try

Done as said but ...No change

---

### Post by DamonChyld on 2008-03-11
Can you run alsamixer from terminal now?

---

### Post by comradelurcher on 2008-03-11
Nope, same answer.........
alsamixer: function snd_mixer_load failed: Invalid argument

---

### Post by DamonChyld on 2008-03-11
Hmm.. most reports I have found through a google seach list this problem with acer laptops running debian but perhaps wading your way through some of their proposed solutions can help you out...
Here is what looks like the most promising link:

 [http://www.debianhelp.co.uk/sound.htm](http://www.debianhelp.co.uk/sound.htm)

Don't let all the code stuff scare you. You don't necessarily have to understand what every line means, just google search error codes and you will get closer to a solution. I wish I could help you out more but I have got to get going here in a few...

Also, use the sound card info you got from lshw, the alsamixer: function snd_mixer_load failed: Invalid argument, and the make/model of your laptop as search parameters

Also also! ;) Don't install packages from the debian link I gave you, use it for problem solving only!! If you install stuff, make sure its for gibbon.

---

### Post by comradelurcher on 2008-03-11
Thanks for your help DamonChyld, if you come up with something give me a tug!!

---

