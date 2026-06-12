---
title: "oss, alsa, esd, arts and sinks? what are these?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-02-27
Exploring around amaroK, I encountered these creatures, and have absolutely no idea what they are, other than being related to sounds. What are they really and what do they do? 

Also, in GStreamer in amaroK I have these osssink, alsasink, artssink,esdsink, jacksink stuff. what are they?

I just couldn't contain my curiosity... (wikipedia only confused me even more) :D

---

### Post by monolegis on 2006-02-27
Generally speaking: Sound drivers/"servers"

[OSS/Linux]("http://www.4front-tech.com/linux.html") is a commercial implementation of the Linux sound drivers that are packaged with the Linux kernel.

[The Advanced Linux Sound Architecture]("http://www.alsa-project.org/") (ALSA) provides audio and MIDI functionality to the Linux operating system. 

[URL="http://www.die.net/doc/linux/man/man1/esd.1.html"]
esd - The Enlightened Sound Daemon[/URL]
DESCRIPTION 
Starts up EsounD, which provides a sound mixing server.

[aRts]("http://www.arts-project.org/") simulates a complete "modular analog synthesizer" on your - digital - computer. The artsd sound server mixes audio from several sources in real time, allowing multiple sound applications to transparently share access to sound hardware.


You can find som more general info [HERE]("http://wiki.linuxquestions.org/wiki/Sound_server").

---

### Post by Jucato on 2006-02-27
Thanks for those links, especially the LinuxQuestions.org (I can never get enough of these Linux links). So combining what I learned there and the little I gleaned from wikipedia, is this about right:

OSS/ALSA - audio drivers?
Arts/ESD/Jack - audio servers?

so in the larger scheme of things:
audio hardware - audio driver - kernel/OS - audio server - audio application

Have I gotten it about right?

How about those *sinks? (osssink, alsasink, artsdsink, jacksink, etc??)

---

