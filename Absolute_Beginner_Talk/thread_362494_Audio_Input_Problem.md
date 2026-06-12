---
title: "Audio Input Problem"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Ciumbi on 2007-02-15
I salute you. This is my first post.
I've installed Ubuntu 6.10 sunday and I came across some problems. I'll present only the audio input for now.

I can't record using Sound Recorder because I can't select any device in "Record from input" section. I've tried to run alsamixer, but I got the following  error:
"alsamixer: function snd_mixer_load failed: Invalid argument"
In Volume Control I have only one Playback tab, I guess it must be also an Recording tab, where I can select the recording device. In File -> Change device I have only one option: Realtek ALC883 (OSS Mixer).

I am using Acer Aspire 5101ANWLMi laptop.

---

### Post by r4ik on 2007-02-15
Edit - preferences ? 
Tick the boxes.

or,

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by Ciumbi on 2007-02-15
I tried that and it didn't work. Anyway, I bootet from the LiveCD and alsaconfig worked, so I reinstalled the operating system. Now it works. I guess I screwed something.

---

### Post by Ciumbi on 2007-02-15
Now, that's interesting. After I installed all the updates and restarted the computer the problem reappeared. Now I can't start alsaconfig from terminal, and I can't select the alsa device from the Volume Control -> Change device. And also I still have the same recording problem, as the OSS Mixer doesn' recognise my microphone.

---

### Post by Ciumbi on 2007-02-16
It seams that no one else had this problem. I guess that even if I find the update responsible for messing with my ALSA driver it will still pop-up in the list at every checkout, and maybe sometime I will install it by accident.
Can someone give me a clue how to prevent that?

---

### Post by Poman on 2007-02-22
I'm having this same problem it seems. I've got a PCI sound blaster card installed as well as the onboard Realtek one. Could this be the problem? The Sound Recorder only wants to choose AC97.

Can't get it to record streaming radio music, though I can hear it fine while it's playing. I do have a record button, and I can play the recording back but there's no sound from it.

---

### Post by sirdarckcat on 2008-06-01
I have the same situation as Ciumbi.

If anyone found a working solution please post it.

They apparently worked something out:
[http://www.linuxquestions.org/questions/linux-hardware-18/realtek-alc883-record-sound-wont-work-597317/](http://www.linuxquestions.org/questions/linux-hardware-18/realtek-alc883-record-sound-wont-work-597317/)

More info:
[http://www.linuxquestions.org/questions/linux-hardware-18/realtek-alc883-microphone-is-not-being-detected.-646281/](http://www.linuxquestions.org/questions/linux-hardware-18/realtek-alc883-microphone-is-not-being-detected.-646281/)

Greetings!!

---

### Post by Ciumbi on 2008-06-02
I had to install a newer version of alsa driver to solve the problem (can't remember which one, maybe 1.0.14 rc3 or 4 ), but now that version is included in Ubuntu 7.10 or newer by default, so I'm not having the sound problem any more.

---

