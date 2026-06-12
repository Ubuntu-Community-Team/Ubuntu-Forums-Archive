---
title: "Wanting to make the switch, sound issues holding me back."
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by GForce64 on 2006-06-01
I'm wanting to take the dive into Linux, but I can't seem to get my sound to work at all. I'm a complete Linux newbie, but I've done a bit of reading and decided to get a Live CD of Dapper Drake. Lo and behold, everything is working except sound.

I have two sound-cards, one onboard and one add-in. The add-on card is a Creative X-Fi XtremeMusic, which to my knowledge has no drivers for Linux. If I am wrong here, let me know.

As such, I'd like to get things working on my onboard sound. Alsamixer tells me onboard is Realtek ALC655 (sounds about right), but I'm getting no sound output. If anyone can help me get my sound working, I would be much appreciative. Also, if I left out any relevant info, please let me know.  Huge thanks in advance.

---

### Post by nalmeth on 2006-06-01
Open the mixer in whichever Desktop Environment you're in, possibly the device is muted or turned all the way down. On my laptop, I couldn't get any sound at all until I turned up PCM. The onboard should be supported out of the box.

I couldn't tell you either way about your other card.

---

### Post by GForce64 on 2006-06-01
[QUOTE=nalmeth]Open the mixer in whichever Desktop Environment you're in, possibly the device is muted or turned all the way down. On my laptop, I couldn't get any sound at all until I turned up PCM. The onboard should be supported out of the box.

I couldn't tell you either way about your other card.[/QUOTE]

Turned everything up all the way, didn't work. Any other ideas?

---

### Post by nalmeth on 2006-06-01
[https://wiki.ubuntu.com/Sound](https://wiki.ubuntu.com/Sound)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

These pages might have some information for you, they are for the older releases (getting documentation up to date is ongoing)
Did you run the gnome mixer? Perhap's alsamixer will be more detailed?

ALT-F2
alsamixer

If you find nothing of help here, try posting a new thread in the Hardware section with any new information you've learned, and posting the step's you've already tried.

I personally know little about sound configuration, as my sound has always just worked. I've never needed to research and fix any problems.

Good luck, hopefully you can make the switch!

---

### Post by GForce64 on 2006-06-01
OK, I just noticed in System >Preferences>Sound that my sound card is incorrectly reported as an nVidia CK804. So...does this mean I'm going to have to hunt for drivers for my onboard sound? I know that the nVidia is not my sound card.

---

### Post by nalmeth on 2006-06-02
Weird. I've never seen that happen before, though as I said I haven't encountered major sound problem's before. And the correct device is not available, is that correct? 

I'm not totally sure how to go about this, but I can say with reasonable certainty that you won't need to hunt down new drivers. You just have to find out how to reconfigure alsa to use the right sound card.

For example, to reconfigure the xserver in the terminal you would run:
sudo dpkg-reconfigure xserver-xorg

now *don't* run this example, but you might be doing something similar to
sudo dpkg-reconfigure alsaxxxyyyyzzzz

Post this new information in a new thread in the hardware section, perhap's there is a simple way to reconfigure alsa.

EDIT: I'm reading a debian-mail listing recommending running alsaconf

try opening a terminal (Applications - Accessories - Terminal) and running
```
alsaconf
```

---

### Post by GForce64 on 2006-06-02
I'm back on Windows right now, but I'll try that later.

---

