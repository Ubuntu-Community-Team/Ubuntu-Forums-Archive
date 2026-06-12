---
title: "What's the difference between the open sound architectures and what windows uses?"
date: 2012-05-09
forum: Any Other OS
---

### Post by venom104 on 2012-05-09
Okay here's my story. I dislike windows so I went with ubuntu. Anyway, I have to add a module in my alsa.conf file to make my ALC887 chipset to play ANY type of sound. I also have to install an alsa module package to get it to work correctly.

On my linux mint debian edition box, that CAN NOT use the deb alsa module package, I had to switch to OSS4 to get it to work. 

Yet...when I boot into windows my sound works fine.

I'm not asking which is better...I just want to understand why it works fine in windows but I have to install extra stuff to get it to work under linux. Do the alsa files contain kernel modules that aren't already loaded into the kernel? What about OSS4, why does OSS4 work and not alsa (on my LMDE box)

---

### Post by jerome1232 on 2012-05-09
My very short answer is: Because ALSA sucks. The driver for your card under alsa are probably bad, buggy, etc...

[COLOR="RoyalBlue"]Did somebody directly below me sneak an edit into my post? At least get the spelling right :P[/COLOR] 

Ah that's probably about right, I've heard bad things about alsa drivers before.

OSS4 is in most ways better than alsa, OSS used to be the standard until they started charging, luckily it's free again.

Personally PulseAudio + Alsa work fine with my chips so I stick to it.

---

### Post by uRock on 2012-05-10
Windows automatically loads proprietary drivers.

I have never had any problems with ALSA.

Moved to *Other OS/Distro Talk*.

---

