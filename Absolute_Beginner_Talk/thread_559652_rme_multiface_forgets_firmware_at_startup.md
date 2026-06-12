---
title: "rme multiface forgets firmware at startup"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by salatmensch on 2007-09-25
greetings,

i'm still having problems with the multiface using the newest alsa drivers. the soundcard works fine when i type in hdsploader. but as soon as i am doing a cold reboot, ubuntu says:

Hammerfall-DSP: wait for FIFO status <= 0 failed after 30 iterations
[   29.284000] Hammerfall-DSP: cannot load firmware multiface_firmware_rev11.bin
[   29.284000] Hammerfall-DSP: couldn't get firmware from userspace. try using hdsploader
[   29.284000] Hammerfall-DSP: card initialization pending : waiting for firmware

where does the hdsp loader want to have the firmware? i even set a link from /lib/firmware/hdsploader to the path specified in the hdsploader readme.

any ideas?

best,

---

### Post by wavesound on 2008-01-28
> **salatmensch said:**
> greetings,

i'm still having problems with the multiface using the newest alsa drivers. the soundcard works fine when i type in hdsploader. but as soon as i am doing a cold reboot, ubuntu says:

Hammerfall-DSP: wait for FIFO status <= 0 failed after 30 iterations
[   29.284000] Hammerfall-DSP: cannot load firmware multiface_firmware_rev11.bin
[   29.284000] Hammerfall-DSP: couldn't get firmware from userspace. try using hdsploader
[   29.284000] Hammerfall-DSP: card initialization pending : waiting for firmware

where does the hdsp loader want to have the firmware? i even set a link from /lib/firmware/hdsploader to the path specified in the hdsploader readme.

any ideas?

best,

Hi How did you get the card to work at all?
I cant get anything to use it.
If I fire up hsdpmixer I can see the input and output but cant set totem or vlc to use it.
really annoying! mean I have to keep the realtek on board system running.

Cheers
Bob

---

### Post by salatmensch on 2008-01-28
well,
i somewhat solved the problem.
first, if the card is not loaded run hdsploader. when this failes, copy the firmware to the position expected in the help-file / error-message of the hdsploader. or find the loading error msg of booting the system.

to run totem with the multiface you might need it to point to using alsa drivers and configure jack to use the multiface. if i remember correctly i replaced totem with another player like xmms. it can use alsa.

if you set the multiface in the ubuntu sound setting then probably jack cannot access the multiface because it's used for dumping system sounds...

best,
salatmensch

---

### Post by wavesound on 2008-01-28
Hi salatmensch
Many thanks for your quick reply.
Yes I did set the multi as the main one to use and jack cannot find/use it.

I cant seem to set anything in Totem at all ( where is the config for this app?)

I'll try the rest.
I'm back to the realtek using VLC

Cheers
Bob

---

