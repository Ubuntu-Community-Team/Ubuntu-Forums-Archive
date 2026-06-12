---
title: "Absolutely no sound - new to linux"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Doublecaret on 2007-11-20
Hello all,

Today I installed Ubuntu 7.10 (Gutsy Gibbon) onto my Sager 2090 Laptop (Compal IFL90) to dual boot with a previous installation of Windows XP. Everything went fine, I got started installing new programs, but then I noticed there was no sound. So, to get out of the way what I did:

Yes: everything is unmuted.
I have updated ALSA.
Aplay gave me this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Lsmod|grep snd:

snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

I went and checked to see that ALSA supported the sound card I have, and they do- but that driver (snd-hda-intel) is not on my system because when I tried sudo modprobe snd-hda-intel nothing comes back.

Afer a few hours of googling and messing around in the terminal I am stumped. Any suggestions? 

Thanks

---

### Post by MaximusTG on 2007-11-21
The modprobe command isn't supposed to give any output, so that's not an error. Your lsmod command lists snd-hda-intel as loaded. Maybe your sound is linked to another channel. Double-click on the sound icon in your tray, and try unmuting and sliding the volume up on all channels (i.e. surround, center etc). That's what did it on my laptop.

---

### Post by mivo on 2007-11-21
Also open a terminal and type *alsamixer* -- make sure the relevant sliders are up.

---

### Post by Boring Bloke on 2007-11-21
> **Doublecaret said:**
> Hello all,

Today I installed Ubuntu 7.10 (Gutsy Gibbon) onto my Sager 2090 Laptop (Compal IFL90) to dual boot with a previous installation of Windows XP. Everything went fine, I got started installing new programs, but then I noticed there was no sound. So, to get out of the way what I did:


I had a similar problem with my old laptop, which had the same dual modem/sound card. 
Try opening /etc/modprobe.d/alsa-base with the command (in a terminal)
```

sudo gedit /etc/modprobe.d/alsa-base


```

And adding  to the end of the file on a new line

```

options snd-hda-intel model=auto

```
If that doesn't work, try model=3stack

I won't promise that it will work, but it's worth a go.

---

### Post by Doublecaret on 2007-11-21
Erg... I tried all the things you guys posted to no avail.... Thanks for trying though :) 

I guess I'll keep at it :/

---

### Post by Doublecaret on 2007-11-22
Bump - still could use any advice.

---

### Post by Doublecaret on 2007-11-22
Well! Let it be known that perserverance and google can get you through any problem.
This combination of code:

sudo gedit /etc/modprobe.d/alsa-base

and adding 

options snd-hda-intel model=toshiba

and then rebooting fixed it up. :KS

for future reference this site helped immensely:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

