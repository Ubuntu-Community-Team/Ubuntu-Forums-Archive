---
title: "What should I do?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by jahisthebalance on 2008-01-28
I have an infrared port on the side of my laptop and it also possesses an S-video out on the back. Does anyone know any cool applications that I could use things for in conjunction with another using Ubuntu?
 Immediately I was thinking of low budget A/V applications using the  infrared port with a remote control of some type, does anyone know if this is possible?   Could it do something like this : :popcorn: or this :guitar:  ?

---

### Post by emarkd on 2008-01-28
check out [http://www.mythtv.org/](http://www.mythtv.org/).  It's in the repositories.  As long as xorg works with your S-Video, myth will take care of lirc for your infrared and with a little config work it should be doable.

---

### Post by jahisthebalance on 2008-01-28
So there is conceivably no limit on input devices then correct? Could I still use any desktop environment once the repositories for mythTV are configured properly?

---

### Post by emarkd on 2008-01-28
I'm not sure what you're asking about the input devices.  And you don't have to configure any repositories for mythtv.  They're in the Ubuntu repositories and you can install it from Synaptic.

---

### Post by jahisthebalance on 2008-01-28
Sorry for being vague anything that can transmit on the infrared spectrum can be the pointing device within a certain degree of precision then?

---

### Post by emarkd on 2008-01-28
Sure, the IR receiver is just that - a receiver.  It receives any IR signal that comes at it.  It's up to lirc to interpret that signal, which may work well and may be a pain to set up.

---

### Post by jahisthebalance on 2008-01-28
lirc, awesome thanks man

---

