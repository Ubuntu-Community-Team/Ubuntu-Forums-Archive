---
title: "Ubuntu 9.10 Karmic bad audio issue on macbook pro 4.1."
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by maffix on 2009-10-29
The new release Ubuntu Karmic Koala have no good audio configuration!:(

First issue.
Frequently I hear a strange sound from speakers like a bump!

Second issue.

When there's no rumor near me, from speakers I hear 	
continuously rumors, but if I move volume switch the rumor stop for 5 second and then starts again.:(

Maybe the new alsa driver do not works well?
I have tried all alsamixer settings without succes!

---

### Post by NoBugs! on 2009-11-03
Sounds like it may be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/367544") or [this bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/305750") that also affects macbooks.

What do you mean by "continuously rumors"?

---

### Post by innandogenous on 2009-11-19
In another forum I found the answer to the problem of the background noise that stops for a few seconds when you adjust the sound:

In, 
```
$ sudo gedit /etc/modprobe.d/alsa-base.conf
```

Comment out the line:

```
options snd-hda-intel power_save=10 power_save_controller=N
```


For whatever reason that solved the problem. It was suggested in another forum and I can't find the link. It worked for me and I haven't had any other noticeable consequences because of it.

---

