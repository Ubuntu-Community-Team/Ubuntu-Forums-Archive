---
title: "No sound in flash"
date: 2007-07-22
forum: Apple Intel Users
---

### Post by Vishaakje on 2007-07-22
Hello, I've just installed ubuntu on my mac pro and have to say I'm extremely impressed with ubuntu :)
Especially now that I've configured everything the way I like it (compiz fusion rocks!). Anyway, the sound (using the digital out) works fine in Audacious using the ALSA sound output. Strange enough using the Analog Output on hw(0,0), but hey it works :P
The trouble is I can't get it to work with flash :(
I've tried:
```
sudo apt-get install alsa-oss
and
ln -s /tmp/.esd-1000 /tmp/.esd
```
Looking in */etc/firefox/firefoxrc* I see *FIREFOX_DSP="aoss"*
Can't I just set it to alsa?
Any thoughts?

Edit: output in the terminal when opening something on youtube:
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
```

---

