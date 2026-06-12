---
title: "Setting up mics"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by 1337sithlord on 2006-01-28
Ok this time I have a normal microphone and it is recognized in the list of sound devices and when i select it, it produces all sorts of feedback when close to the speakers, so it is working but nothing will capture.

In sound recorder and audacity it just gives empty sound whenever i talk into the mic and i put all the volumes at maximum in the volume control.  Does anyone have any ideas?

---

### Post by christhemonkey on 2006-01-28
go into a terminal (right click 'open terminal')
alsamixer
press F5 to view all options,
look for microphone and select it by pressing space (if it says its muted press M)

---

### Post by eriefisher on 2006-01-28
In audacity I always forgot to switch from line in to mic in and visa vera. Don't know if this helps but I know I did alot of head scratching before I remembered but thats me and I'm a moron.

eriefisher

---

### Post by az on 2006-01-28
I had to enable the +20 decibal boost option in the gnome volume meter preferences to hear stuff from a cheapo microphone.

---

### Post by 1337sithlord on 2006-01-29
I tried all of that and it didn't work but thanks anyways.

---

### Post by 1337sithlord on 2006-01-30
Oi, I got it to work with

```
esd
```

It works perfectly now.  I didn't even use the mic boost.  It sounded weird in Audacity but that's because the frequency was too low and I adjusted it to be perfect.  Its actually quite a good feature since I have the voice of a little kid and need to sound like soldiers and stuff when making my shockwave game.

---

