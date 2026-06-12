---
title: "No Sound"
date: 2013-09-12
forum: Any Other OS
---

### Post by michael67 on 2013-09-12
I have the HP dv6707us with Linux Mint 15 and my sound does not work and I don't know how to install the drivers, please help

---

### Post by mymoodz on 2013-09-13
do you know which sound card it has installed in it.I am not an expert but i usually would first see which is the hardware and then start looking for its driver.

---

### Post by Impavidus on 2013-09-13
First check: has the sound been muted? This is slightly less trivial than it may seem. Using pulseaudio and/or alsa? To be sure try them both, that once was a nasty problem on my laptop. Terminal commands```
alsamixer
pavucontrol
```In alsamixer you can use the arrow keys and press m to (un)mute. There must be a GUI way too, but I don't know how.

If it's driver related, you can find the audio chipset using```
lspci | grep Audio
```

---

### Post by oldos2er on 2013-09-13
Moved to Other OS/Distro Support.

---

