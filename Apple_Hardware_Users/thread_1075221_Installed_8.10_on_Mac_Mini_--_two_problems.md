---
title: "Installed 8.10 on Mac Mini -- two problems"
date: 2009-02-20
forum: Apple Hardware Users
---

### Post by sublimity on 2009-02-20
Hello all -

I just installed Ubuntu 8.10 AMD64 on my Mac Mini - it's a 1.83ghz Core 2 Duo model with a gigabyte of RAM.  I'm dual-booting with OS X using rEFIt, and everything there works very well.  However, I have two problems:

1: Sound.  When my Logitech USB headphones are plugged in, I can hear audio from video and music files (albeit entirely too quietly).  That's when I have the "Sound" preferences pane set to the OSS version of "Logitech USB Headset USB Audio."  It's too quiet, but it's there.  But if I try to set it to play through the computer's built in speaker or through the output, I don't have any luck.  If I set it to "HDA Intel STAC92xx Analog (OSS)" (there are three of those in the context menus; the first two work) I can hear the sine wave test tone, but nothing else.  This is the case whether my USB headset is plugged in or not.

2:  Wireless.  I've connected several times to my WPA-protected wireless network, but it's difficult to do.  I sometimes have to try reconnecting repeatedly, and sometimes it simply won't connect.  This happens even though several laptops and desktops (both Mac and Windows) are able to connect without problems.


I think that I'm really going to enjoy using Ubuntu.  It's very slick and user friendly, and lets me dabble with something different.  However, to fix the audio problems (being able to playback over normal speakers, and at a high enough volume) and the wireless network problem would be fantastic.

Suggestions?
  -  Sublimity

---

### Post by cyberdork33 on 2009-02-20
> **sublimity said:**
> 1: Sound.  When my Logitech USB headphones are plugged in, I can hear audio from video and music files (albeit entirely too quietly).  That's when I have the "Sound" preferences pane set to the OSS version of "Logitech USB Headset USB Audio."  It's too quiet, but it's there.  But if I try to set it to play through the computer's built in speaker or through the output, I don't have any luck.  If I set it to "HDA Intel STAC92xx Analog (OSS)" (there are three of those in the context menus; the first two work) I can hear the sine wave test tone, but nothing else.  This is the case whether my USB headset is plugged in or not.you should be trying to use the ALSA devices, not the OSS devices. You can make sure that the also mixer levels are turned up and unmuted by running:
```
alsamixer -c 0
```
 
> **sublimity said:**
> 2:  Wireless.  I've connected several times to my WPA-protected wireless network, but it's difficult to do.  I sometimes have to try reconnecting repeatedly, and sometimes it simply won't connect.  This happens even though several laptops and desktops (both Mac and Windows) are able to connect without problems.
Unfortunately this has been a pretty common problem with no sure-fire fix. What card are you using? (use lspci to get information)

---

