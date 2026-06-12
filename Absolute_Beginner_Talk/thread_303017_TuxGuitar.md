---
title: "TuxGuitar"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by guitarmaniac on 2006-11-19
Hey everyone,
I discovered Tuxguitar the other day which seems like a great solution to guitar pro for linux.
Anyway i installed the .deb pack from sourceforge and i can't get any sound out of it!?!
I also installed the alsa plugin from that site and that didnt fix anything.
I'm running edgy and i have been playing around with ubuntu since breezy came out, but im not a tech head.
Any help would be greatly appreaciated!

---

### Post by D_jmc on 2006-11-19
Does the file play? Do you get an error message?

I just installed it, and tried to play a GP3 file and it gave in error saying  that it couldn't open a soundbank and i realised that I had Rythmbox open. Hopefully its something as simple as that.

I take it that Ubunto(edgy) wont let you have more than one access the soundcard, or if there is a way I dont know it.

---

### Post by nalmeth on 2006-11-19
Have you seen this page?
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

> If you are planning on using MIDI at all, you will want to load the ALSA sequencer module.  

sudo modprobe snd-seq

To have your system load it at bootup, you have to add it to the /etc/modules file.  

sudo su -c 'echo snd-seq >> /etc/modules'
 [B]

Timer Resolution[/B]

  The Ubuntu kernel currently is set to 250Hz timers, which is insufficient for MIDI. We can correct this:  

sudo sysctl -w dev.rtc.max-user-freq=1024

To make it persistent across reboots, you need to add a line to the /etc/sysctl.conf file.  

sudo su -c 'echo dev.rtc.max-user-freq=1024 >> /etc/sysctl.conf'


---

### Post by guitarmaniac on 2006-11-23
hmmm, still nothing.
It plays the guitar pro songs with no errors, it just doesnt make any sound!
I really dont know whats wrong!
No other programs should be using the soundcard, and i tried all the above commands!

---

### Post by guitarmaniac on 2006-11-23
ok, turns out it was just the ALSA plugin!
now its seems to be working ok.
I do miss the guitar pro "real sound engine" though.

---

