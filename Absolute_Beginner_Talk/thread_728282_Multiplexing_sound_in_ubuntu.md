---
title: "Multiplexing sound in ubuntu?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by jprophet420 on 2008-03-18
It seems that it is not possible to run more than one sound app at a time in all the distros I've used, however I've never used anything but a generic soundcard driver. For example, i would like to be able to run ventrilo and xmms, or even a movie or game...

Is it possible that updating drivers will work? And if its not an issue that can be fixed with drivers, is it possible to run an onboard soundcard and a pci card in conjunction?

---

### Post by PurposeOfReason on 2008-03-18
Dmix should let you do that. I'm not sure with ubuntu, but try sudo aptitude install dmix dmixer. It shoudn't even be a package, it should just exist. Then create a /etc/asound.conf and put this in it.

```
#/etc/asound.conf start:
pcm.!default {
    type plug
    slave.pcm "dmixer"
}


pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 8192
        rate 44100   #many new cards are 48000 only
    }
    bindings {
        0 0
        1 1
    }
}

ctl.dmixer {
    type hw
    card 0
}

#end.


```

---

### Post by jprophet420 on 2008-03-18
hmm, i followed the instructions, but nothing happens. there is no new mixer, no app to open or anything. no multiplexing either. thank you for the help so far.

---

