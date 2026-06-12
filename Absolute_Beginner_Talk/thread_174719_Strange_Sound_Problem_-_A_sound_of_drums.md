---
title: "Strange Sound Problem - A sound of drums"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by Chucky G on 2006-05-12
When I hooked up the sound to my system when running Ubuntu...there is a sound like drums. 

No...I am not joking. :-? 

It's coming from Ubuntu because when I adjust the volume, it comes and goes.

:confused: 

It's great that it found the sound device....but what now?

Anyone else have this problem?

---

### Post by mostwanted on 2006-05-12
You're saying it's a constant thing? When you reach the login screen (GDM) there should be a sound of drums, but it's only played once (lasts about ½ second). I've never heard of it refusing to stop.

---

### Post by macdo on 2006-05-12
Check the plugs and cables, to start with.
When you say drums, do you mean boom - boom (kettle drum), or brrrrrrrrrrrrrrrrrr (roll on the snare)?
(sorry, graphical representation of sound had never been my forte!)

---

### Post by Mustard on 2006-05-12
Have you got a VIA motherboard?  I've had this problem myself.  I havent totally worked out what causes it, but I managed to get around it.  For a while I was starting up with the irqpoll kernel option, and then I disabled the sound server in Ubuntu and stopped using the irqpoll kernel option.  Things seem to be back to normal now.

Would you describe it as an 'infinite looping drumbeat' at the gdm login screen?

---

### Post by syracusepc on 2006-05-14
I'm having the same problem, on a Gateway G6-400 machine. It's the start up drums doing a continual/rolling drum beat? Is ALSA having a problem configuring me onboard sound?
Do I need to add a PCI sound card to get around this?
:confused:

---

### Post by davidpeele on 2006-08-08
Same thing here...
That tom tom is cute for the first 3 or 4 minutes, then I want to rip my ears off.  :mad: 

The system endlessly loops any sound played. try to play a sound with the media player and it sounds like I am playing a CD that has been through the microwave oven. then it just loops the last 1/2 second or so of sound until it gets something new to loop.

VERY annoying. Ubuntu is cool and all but...

I have got to fix this (besides muting the volume). 

It look like I have an Allegro ALSA PCI 125D 1988 sound card.

Any help would be great! [-o<

---

