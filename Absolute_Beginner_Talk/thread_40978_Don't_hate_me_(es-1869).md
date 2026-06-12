---
title: "Don't hate me (es-1869)"
date: 2005-06-11
forum: Absolute Beginner Talk
---

### Post by heltinde on 2005-06-11
Hi folks

I got this "wonderful" and "famous" onboard soundcard ess audiodrive 1869 (Compaq). I got it to work - partially. It sounds awful and the music level (cdplayer) is rather low. There is no speaker icon in the right top of the screen.
It doen't work after a restart. I tried this:

I made a file in /etc/modprobe.d/:
alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388
fm_port=0x330 irq=5 dma1=1 dma2=0

And then did this (as root)
modprobe snd-es18xx
/etc/init.d/alsa restart

This doesn't make it work, but now I get the message 'start esd in a terminal'. So I did, and now I got sound as described above.

How do I get to use alsa instead of esd? And why do my changes disappear after a reboot?

---

### Post by tread on 2005-06-11
To use alsa, kill esd (or rather, dont start it) and then change the output plugin in xmms/beep-media-player (whichever you use) to alsa. You can also change default gnome settings to use alsa, though I dont remember where in the settings you can change this!

---

### Post by heltinde on 2005-06-11
[QUOTE=tread]T... and then change the output plugin in xmms/beep-media-player (whichever you use) to alsa. You can also change default gnome settings to use alsa, ...[/QUOTE]

Can you explain it a bit more simple? I don't know what xmms is. - And if I don't start esd there is absolutely no sound at all.

---

