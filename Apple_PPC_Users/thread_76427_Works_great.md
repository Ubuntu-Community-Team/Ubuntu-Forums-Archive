---
title: "Works great"
date: 2005-10-15
forum: Apple PPC Users
---

### Post by pvz on 2005-10-15
Well, let me be the first then to say all works well on my iBook G4 with Kubuntu so far. I made alsa the default and put
```
pcm.swmix {
        type dmix
        # any unique number here
        ipc_key 313
        slave {
                pcm "hw:0,0"
                # these settings may require tweaking for different sound
                # cards; this is for the Powerbook's built-in snd-powermac
                # probably not required at all for well-behaved cards...
                period_time 0
                period_size 1024
                buffer_size 8192
                # mentioning rate fixes wrong speed/pitch in native ALSA stuff
                rate 44100
        }
}

# this makes OSS emulation via aoss default to using dmix, allegedly
pcm.dsp0 {
        type plug
        slave.pcm "swmix"
}

ctl.mixer0 {
        type hw
        card 0
}

# this makes native ALSA apps default to using dmix
pcm.!default {
        type plug
        slave.pcm "swmix"

```
in /etc/asound.conf and replaced gstreamer-engine with xine-engine in amarok, so now I have working sound from multiple sources.
sleep seems to work as well, nice.

---

### Post by daller on 2005-11-09
Nice!

---

