---
title: "No sound on PowerMac G4 466MHz"
date: 2006-11-18
forum: Apple PPC Users
---

### Post by tom.3xm on 2006-11-18
Hi folks,

I am nearly lucky with my first Ubuntu installation 6.10 for PPC, but one thing is inacceptable: I get no sound *sigh*

I tried a lot of things reading me through the forums, here some infos I collected:

* Listing PCI sound cards ends up with no result.
* Here's my CPU:
```

mac@powermac:~$ grep motherboard /proc/cpuinfo
motherboard     : PowerMac3,4 MacRISC2 MacRISC Power Macintosh

```
* Here's a lsmod someone suggested to run:
```

mac@powermac:~$ lsmod | grep snd
snd_powermac           49916  1 
snd_aoa_i2sbus         24516  0 
snd_pcm_oss            54048  0 
snd_mixer_oss          22144  1 snd_pcm_oss
snd_pcm                95556  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd_page_alloc         11368  1 snd_pcm
snd                    69940  8 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  1 snd
snd_aoa_soundbus        7972  1 snd_aoa_i2sbus

```

I worked a lot on Macs but I am not really sure which soundcard my old Mac has?

I build in a bigger hard drive (120GB), added 1.5GB of RAM, so I am really lucky with Ubuntu and my old "guy", but sound should really work ... Any help is really appreciated, until we will read us again,

Tom

---

### Post by trash on 2006-11-19
Same machine and same problem here, after rebooting I always have to open the volume control and check 'pc speaker' box

---

### Post by blitterfly on 2006-11-19
I had this same problem with my G4 when I first installed. I fiddled with a lot of stuff to get it working, so I'm not exactly sure, but I think these are the steps that did the trick:

1.) Go to System -> Preferences -> Sound. On the Devices tab, make sure all your playback devices are set to ALSA.

2.) Open a terminal and run 'alsamixer' - make sure none of the output channels are muted and have the volume turned up. (If you've not used alsamixer before you can hit ? to get a list of commands.) Hit Esc to exit once you've done that.

3.) Again in the terminal, run 'sudo alsactl store'.

You should be good to go at that point... at least it worked for me, anyways. One thing that's kind of annoying is every time I reboot the master channel is muted again, and I have to go up to the little speaker icon and uncheck Mute.

---

### Post by tom.3xm on 2006-11-20
Hi folks,
thanks for replying! :-)

I solved "my" problem in a easier way:
Problem was not Ubuntu or the installation, the problem was my hardware! I had Apple Pro speakers connected to my G4 and there was no sound at all (but they worked properly because I got that typical wave sound each startup of the machine). Last night I reinstalled Ubuntu 6.10 while having my headphones conncted by accident as well as the Apple Pro speakers - and I had sound! :-) I removed the headphones, Apple Pro speakers are with no sound again. I plugged the headphones again --> Sound!
I haven't figured it out, might have something to do with the mixer, active "headphone" or "automute", had no time to check it, but when I connect Apple Pro speakers AND the headphone (or even something blind pugged into 3.5 mm audio connector) I have fully sound on my Apple Pro speakers! :-)

Hope this could help you too,
greets
Tom

---

