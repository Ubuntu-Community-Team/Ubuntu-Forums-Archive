---
title: "unable to record sound"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by rwrouns on 2008-03-16
I have a gigabyte main board with realtek azalia audio chip, running ubuntu 7.10.  Playback is fine but sound recorder and audacity do not recognize microphone or line input for recording.  They are not muted and input signals pass through the chip coming out the output. The apps just won't record them.  What should I do.

---

### Post by angry_johnnie on 2008-03-17
I think you might need to install jackd and jack-tools.  Look for them in synaptic.  There may be more jack-related things (jack-rack, jackbeat, and so on) but I don't think you'll need those.  This is what synaptic has to say about jack:
> 
JACK allows the connection of multiple applications to an audio device,
as well as allowing them to share audio between themselves.

I remember having to use Jack in Ubuntu Studio in order to record things and to use Creox. 

It may help you. :-)

---

### Post by rwrouns on 2008-03-19
Thanks for the reply.  Before I could try it, I stumbled across a partial solution.  I think I installed the ALSA -OSS package through Synaptic (I checked ALSA-OSS in Synaptic and it did its thing) and also checked "capture" in the ALSA Mixer preferences which brings up the Record tab.  At this point I can record, but the mixer bar in Audacity does not function, I have to set levels with the ALSA mixer.  The only other issue is that playing back a recording with Audacity gives data drops which I assume are the cause of random pops.  When I export the recording to WAV format, store the file and play back with another app such as Totem, there are no data drops.  Any clues on how to get the mixer bar working in Audacity?

---

