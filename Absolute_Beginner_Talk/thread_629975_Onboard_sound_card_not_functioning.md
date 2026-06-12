---
title: "Onboard sound card not functioning"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Emperor.Travis on 2007-12-02
Alright, I've got another problem already. For reasons that are beyond me Ubuntu doesn't want to play nice with the crappy onboard sound card in my machine. 
 I went into the sound preference file and tried to do the sound playback test, and all the other tests it'd let me do. For everyone I got this message. "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing." 
 So then I went and into terminal and typed <lspci -v> to bring up the list of devices in my computer. This is what it said for my sound card, "00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 0126
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Memory at fe300400 (32-bit, non-prefetchable) [size=512]
        Memory at fe300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>" 

But when I typed <aplay -l> it came up saying "device_list:204: no soundcards found..." 

Anyone know what to do?

---

### Post by victorgreen on 2007-12-07
Try searching around the ubuntu wiki and the ALSA site to see if your sound card is supported at all. There is a slight chance its not, but most everything is by now. Beyond that you could try downloading the latest version of alsa and compiling it. There are a couple guides for that on the forum if you search around.

---

