---
title: "Sound in headphone but not in Speakers!"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-18
I have this problem......I can hear sound only in my headphone/mic but not out of my speakers. How would I configure it so I get sound out of my speakers.

Thanks

---

### Post by Metacarpal on 2006-07-18
How do your speakers connect?  Is it through the same jack as your headphones, through a different line-out jack of the same type, or a different setup?

---

### Post by zxcvbnm on 2006-07-18
My headphones go into 2 jacks(One for headphone the other for mic) in the back of my PC and my Speakers are connected to a volume controller which is also connected to the back of my PC

---

### Post by Skia_42 on 2006-07-18
So is the volume controller connected to your computer via 3.5mm jacks? (Standard headphone jacks)[IMG]http://www.modsynergy.com/Modsynergy%20files/A%2BGPBheadphones-jacks.jpg[/IMG]

---

### Post by x64Jimbo on 2006-07-18
I'd connect the headphones into the speakers and the speakers into the headphone port on the back of your PC. Use what works ;)

---

### Post by OU812 on 2006-07-20
So you're tyring to find a way to keep everything plugged in? Maybe you have a volume control set to mute or too low. Try running from the terminal

alsamixer

check the settings for mute and volume level. When everthing is adjusted, hit esc. Then enter

sudo alsactl store

john

---

