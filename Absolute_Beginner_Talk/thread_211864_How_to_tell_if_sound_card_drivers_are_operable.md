---
title: "How to tell if sound card drivers are operable?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-09
A few days ago I asked how to tell whether nVidia drivers were actually driving the display.  I got two great answers on using a CLI command to discern this.  It was sort of an oddball command that doesn't appear much in guides.

So today I'd like to ask: How do I tell if my sound output is being driven by the appropriate software?  I really doubt that the drivers for my SoundBlaster Live 24-bit card were installed by Ubuntu at Ubuntu installation.  Maybe -- but how can I tell for certain?

Thank you!!

---

### Post by harishg on 2006-07-09
Did you try playing any music ? Try playing an audio cd ?

---

### Post by Apple 101 on 2006-07-09
You may need to select your Creative SB Live 24-bit card - I had to select mine.  In Gnome: System --> Preferences --> Sound.  Check the default card in the box at the bottom of the window.

---

### Post by Susan.Desanco on 2006-07-09
Apple101 --

Thanks for that.  I checked the dialogue you mentioned and it looks like my default sound card is listed as CA0106, which Googles out to be my SoundBlaster Live 24-bit LS card.

Although according to NewEgg reviews of this particular card, linux is unable to harness the 7.1 output of this card without the assistance of something called alsamixer.

---

### Post by woedend on 2006-07-09
open a terminal and type
alsamixer

there you are :p
just use the arrow keys to move left to right, a description is listed at the top, use the 'm' key to turn things on/off

---

### Post by jdunn on 2006-09-27
Many thanks.  I just bought a SB Live 24-bit to replace my on-board sound and I couldn't get the mic to work at all.  I ran alsa mixer and all I had to do was crank the volume up on the mic input and it works fine.

---

### Post by bodhi.zazen on 2006-09-27
You will hear music :)

---

