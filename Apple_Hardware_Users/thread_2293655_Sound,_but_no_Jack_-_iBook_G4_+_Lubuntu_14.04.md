---
title: "Sound, but no Jack - iBook G4 + Lubuntu 14.04"
date: 2015-09-06
forum: Apple Hardware Users
---

### Post by Zestie Bumwhig on 2015-09-06
I am trying to make this old iBook G4 useful to me. I'd be satisfied with wireless, a non-glitching screen, and the audio programs Pure Data and Supercollider.

I got sound to work, though it wasn't easy - I had to download a new patch "snd-aoa-device-id-38-fix", use DKMS to rebuild part of the kernel... I'm not really sure what I'm saying here, sorry. It was all based on this thread:

[http://ubuntuforums.org/showthread.php?t=2209340](http://ubuntuforums.org/showthread.php?t=2209340)

Eventually, it worked (many thanks Adam Smith!). Pure Data works, but Supercollider requires Jack... and for the life of me, I can't get Jack to work. At first, using qjackctl, I had D-Bus errors; I turned off "Enable D-Bus Interface" in "Misc" of qjackctl's Setup, and now I have the (more common!) "Cannot connect to server socket err = No such file or directory".

When I try to start from a terminal, with:
```
$ jackd -d alsa -r 44100
[...]
JACK server starting in realtime mode with priority 10
Bus error (core dumped)
```

In case you're wondering - I AM a member of the "audio" group; I don't have PulseAudio installed; I've tried "default" and "SoundByLayout" in qjackctl's Setup - Interface.

```
$ aplay -l
card 0: SoundByLayout [SoundByLayout], device 0: Master []
Subdevices: 1/1
Subdevice #0: subdevice #0
```

I'd love any advice. I'd also considering installing a different (?)ubuntu / Linux in case audio works better without some of these crazy twists.

Thanks!

---

### Post by thomas62 on 2015-09-07
Hey

I can;t help with the jack, getting supercollider to work sounds cool though.

You could try 12.04 if you try a different install. That's all the advice I've got.

You could also look at this

[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373)

Taken from here:

[https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr](https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr)

---

### Post by dand1972 on 2015-09-07
Which version of jackd do you have installed, jackd2 or jackd1?  If you have jackd2, try replacing it with jackd1.

---

### Post by Zestie Bumwhig on 2015-09-08
Thanks for the tips, you two. After trying to get Jack to work, I seem to have smashed my audio altogether. Perhaps my card wasn't Device 38 (which the patch was made for), and it was mere dumb luck that had it working at all?

(thomas62, I had been following the PowerPC Known Issues & the suggested patch - no idea why it worked temporarily.)

Anyway, I'd hoped to not have to re-install and re-configure again, but I'm now lost at how to get sound to work... so 12.04, here I come!

(and, dand1972, it was jackd2. If my sound worked, I'd certainly try jackd1!)

---

