---
title: "Sound card configuration problems"
date: 2007-08-30
forum: Apple PPC Users
---

### Post by momcmanus on 2007-08-30
Here's what's going on:

I have an M-Audio Delta 44 card installed. ALSA and JACK are both installed. 
I also have qjackctl installed and can open and start the JACK server. 
Here's the problem: both when I start the JACK server and
when I turn up the DAC and DAC 1 channels in the ALSA mixer this
produces  a pulsing sound through the speakers. Similar to a
"click-click-click-click-click-click..." I also hear this noise when clicking the "test"
buttons under the Sound preferences app.

Any ideas as to what the problem might be? Google searches haven't
turned up anything useful which is why I turn to you all now. Is this a
problem with not having the realtime kernel (something I've been trying
to install, but haven't had success following the instructions on the
Ubuntu site)?

It seems as though the system can see the card, it recognizes it as an ice1712 chip,
which is correct as far as I know. It seems like there's something global I'm missing
since even system sounds come out all garbled.

Thanks for the help!!!

---

