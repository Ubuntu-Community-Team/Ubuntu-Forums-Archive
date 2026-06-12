---
title: "Sound issue: 5.1 not working"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by TheShocker on 2007-12-09
Hello,

For some reason everything plays in only 2.1. I have a 5.1 set-up which works just fine in windows. It's an nVidia chip built into my motherboard. I have tried fooling with the settings and adding tracks to no avail in the volume control window. Can anyone help me get my 5.1 working?

```
sudo lshw -C sound
[sudo] password for seth:
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

```

---

### Post by TheShocker on 2007-12-11
Anyone?

---

### Post by Daveth on 2007-12-11
this

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

suggests this 

"webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by sudo nano /etc/modprobe.d/alsa-base and adding this as the last line: "options snd-intel8x0 ac97_quirk=3"

might be worth playing with. Have you also opened up alsamixer and poked about with its settings?

---

### Post by TheShocker on 2007-12-12
I've tried fooling with alsamixer. No luck there. I'm kind of new to Ubuntu and Linux in general so I'm not too comfortable playing with what you suggested at this point. I have an AMD 64 X2 4200+ with an nForce4 board. That post said the user had an Intel. I'm afraid I'll just make the problem wore if I try that.

---

### Post by TheShocker on 2007-12-13
Well I tried doing what that thread suggested.

```
sudo nano /etc/modprobe.d/alsa-base
```

and adding this as the last line:

```
"options snd-intel8x0 ac97_quirk=3"
```

(I did not include the quotes.)

Still no 5.1.

---

### Post by TheShocker on 2007-12-14
Hmm. After doing a restart, now I have no sound whatsoever. Just a clicking noise. I made a new thread here for this issue: [http://ubuntuforums.org/showthread.php?t=635674](http://ubuntuforums.org/showthread.php?t=635674)

---

