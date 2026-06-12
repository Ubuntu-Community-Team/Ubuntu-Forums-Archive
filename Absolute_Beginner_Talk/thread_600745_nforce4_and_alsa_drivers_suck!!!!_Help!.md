---
title: "nforce4 and alsa drivers suck!!!! Help!"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by jaybombalous on 2007-11-02
Ok, so I m happy with this gutsy 64 bit OS install. everything works wonderfully except for the damn sound.

The sound is awful, in feisty and gutsy 32-bit the sound with the alsa drivers was **great**(so great u could even say it was **exceptional**). In fact it was one of the reasons I made the final jump to linux.

Once I switched and moved to 64 bit gutsy all of a sudden the sound quality drops through the floor and its **quiet** all of a sudden. What I mean by that is I have all my volume controls **maxed** and it may be playing at 25db if I am lucky. With the need to crank the volume controls to max values it has injected noise into the signal, making for an awful sound experience.

So what happen? is the nforce4 that bad of an audio controller or is it something else that I just haven't configured correctly. So far I haven't configured anything, so there is nothing I have done to get this shitty *** sound quality. Its straight out of the box ubuntu or nvidia that is causing my problems and I need a fix.

---

### Post by jaybombalous on 2007-11-02
as a follow up, isn't possible to use more then one sound source with alsa driver? Because I can't and I am now sure this is part of my problem.

Anyone for a how-to on reinstalling alsa drivers on a 64 bit gutsy install?

---

### Post by jaybombalous on 2007-11-02
now synaptic broke, I have the cd I nstalled gutsy with in the cdrom. It even pops up in nautilus that its been mounted as it displays the contents, yet somehow apt-get doesn't agree.

```
jasin@ubuntu:~$ sudo apt-get install -f
[sudo] password for jasin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsamplerate0
The following NEW packages will be installed:
  libsamplerate0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0B/110kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)'
in the drive '/cdrom/' and press enter
```

anyone?

---

### Post by mdpalow on 2007-11-02
I can't help you with this, but I can say that before installing Gutsy, I did some quick research on the 32bit vs. the 64bit and from what I read, most of the users recommended staying with the 32bit 'cause of memory, some other things, and the fact that performance was that much better.

Based on that, I stayed with the 32bit. I certainly don't know what you're doing to suggest you switch to 32bit again, but maybe if you don't actually need the 64, you might consider going back to 32 and especially since your sound was so much better.

Just something to ponder....

---

