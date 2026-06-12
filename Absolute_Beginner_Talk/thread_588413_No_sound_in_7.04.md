---
title: "No sound in 7.04"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-10-23
Hey guys. I see that alot of people are having trouble with sound in 7.10, but I am in 7.04. I have a Realtek ALC660 6-channel audio Compliant with HD specification thing (I'm not sure what you'd call it, sorry for my ignorance towards this) on my motherboard. What can I do to make my sound work? Thanks.

---

### Post by Martje_001 on 2007-10-24
What's "trouble"? Doesn't it work at all? Or is it lacking? And do you use stereo or 5.1?

---

### Post by realvz on 2007-10-24
double click the volume icon in gnome panel...and goto prefernces and select all the items./..then click ok...

then unmute all the devices there and see if it helps./

---

### Post by drndrw on 2007-10-24
Well, I tried that, but I'm still not getting anything. I switched the sound from the alsa to my motherboard's integrated. What now?

---

### Post by Ubuntized! on 2007-10-24
try and type alsamixer at the prompt and see what comes out!
Edit:
and of course let us know!

---

### Post by drndrw on 2007-10-24
Well, I played around in alsamixer. Still nothing :(. What settings do I need becasue I was just messing around?

---

### Post by Ubuntized! on 2007-11-04
Well I am not this great expert but you should make sure you don't have any 'MM' below any channel marked with, for example, master, center, or PCM or below anyone of the leftmost columns!
Second thing, what fixed my problem was (assuming that you don't want a 27.5 channels surround sound:lolflag:)a little string that should be put into the /etc/modprobe.d/alsa-base file under the "section" ""# Prevent abnormal drivers from grabbing index 0""
but there is a problem right now because I've got my laptop repairing! My touchpad is out of order:) and so I don't remember what you should write...feel sorry :(

---

