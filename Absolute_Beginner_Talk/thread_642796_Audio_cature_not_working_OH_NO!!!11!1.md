---
title: "Audio cature not working OH NO!!!11!1"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-12-17
So All my sound playback works great. But for some reason my sound capture isn't. I have a "**Realtek ALC883**" When I go into my sound setting the driver defaults to **"ALSA - Advanced Linux Sound Architecture**". I've also tried different ones through the pull down box, as follow, "**ALC883 Digita**l", **"ALC883 Analog**", "**OSS - Open sound system**" They all give me the same error "**gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing**."  Any help would be greatly appreciated. Thanks in advance for help. 


:popcorn:

Forgot to mention, My sound card is an ALC883, and I know my mic works, I've tried it on windows because I have dual boot.

---

### Post by supergrover1981 on 2007-12-19
Hi Comzee,

Not sure if this helps, but have you enabled audio capture in volume control? Specifically:

1.) In a terminal, type "gnome-volume-control"

2.) Edit-->Preferences

3.) A "recording" tab should pop up. Click on that, slide the volume control up from zero, and click the microphone icon so that there is no red cross through it

Hope this helps,
                       - SuperGrover

---

