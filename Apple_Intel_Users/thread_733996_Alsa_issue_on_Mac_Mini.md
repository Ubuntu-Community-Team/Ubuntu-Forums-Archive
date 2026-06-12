---
title: "Alsa issue on Mac Mini"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by kmand on 2008-03-24
I'm running Gutsy on an Intel Mac Mini. The audio has me a bit puzzled.

I'm using the headphone output to get audio output to a TV. When I bring up Alsamixer the Master and PCM controls do nothing, only "front" controls the volume.

There are a couple of problem with this related to Mythtv.

First the only volume control in Myth itself is by configuring it to use Master or PCM.

Second, even if I externally set "front" to 100% with alsamixer, the volume is still low compared with the other sources to the TV., which makes source switching problematic.

It's not a hardware issue. Vlc playing the same input as myth can put out a normal volume level. Vlc has an internal volume control independent of the mixer. At midlevel it puts out about the same volume as myth, but at max value it gives a volume level similar to my other TV's sources.

The straight Ubuntu/Alsa question: Is there a way to configure Alsa Mixer so Master controls the analog output, and is there a way to increase its output?

Beyond that I'm wondering what VLC does that Myth doesn't to get the louder volume.

---

