---
title: "Turning off PC speaker?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by dgbearcat on 2008-02-03
Unless I manually go in into my sound preferences and turn the PCI down all the way, my PC speaker always plays, even if I use my hard buttons to mute or turn down the volume. 

Any way to turn off the PC speaker completely without messing up any of my other sound?

---

### Post by jrib on 2008-02-03
System -> Preferences -> Sound -> System Beep tab

uncheck "Enable System Beep"


Does that do what you want?

---

### Post by wolfen69 on 2008-02-03
if that doesnt work, you can always open up the computer and physically disconnect your speaker from the motherboard.

---

### Post by dgbearcat on 2008-02-03
> **_jason said:**
> System -> Preferences -> Sound -> System Beep tab

uncheck "Enable System Beep"


Does that do what you want?

Hmm, no. I'm not talking about system beeps. 

I mean my laptop (inspiron 9300) uses the pcm (or at least some internal speaker) to play things. For example, if I mute "main sound" and try to watch some random movie on youtube, the normal speakers stay silent, but I hear the sound coming from "within" my computer. 

It's not actually the PC speaker because that's muted already, and using the PCI scroll bar makes it stop, but it also turns my regular sound down to nothing. Maybe I just need updated drivers, but I haven't quite figured out how to get new drivers for particular devices yet.

---

### Post by dgbearcat on 2008-02-03
> **wolfen69 said:**
> if that doesnt work, you can always open up the computer and physically disconnect your speaker from the motherboard.

Thaaaat would not be so preferable, if there were any way to do it soft instead of hard.

---

### Post by dgbearcat on 2008-02-04
Ok, fixed it myself and thought I'd put it here:

Went to terminal and did "alsamixer" and went to the second option of "main mono" and turned it all the way down. Fixed!

---

### Post by LowSky on 2008-02-04
your BIOS could have a setting for turning off a PC speaker as well

---

