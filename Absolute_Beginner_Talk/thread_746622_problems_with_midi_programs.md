---
title: "problems with midi programs"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-04-05
Okay so last night I got this cool program called guitar speed pro and it uses midi. I run it using wine. It was working great last night and then when I went to use it today it works for a minute or so then just closes. I have noticed also that the GTick metronome no longer works. when I try to start it it says

Couldn't start metronome.
Please check if specified sound device
and sample file are accessible.

The only changes I remember making were installing a soundfont and deleting files off of the desktop that I used to install the program


also, when I run winecfg from a terminal this appears in the terminal

```
user@computer:~$ winecfg
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
```

---

### Post by shawnjones on 2008-04-05
Sometimes when I had problems with MIDI and multi track audio under Ubuntu, I find that a good old restart does the trick. Perhaps a better option would be to find a MIDI program that runs under native Ubuntu and eliminate wine all together.

---

### Post by elchico04 on 2008-04-05
ahh! i hate this. now the program works. I think im just going to leave it open all the time because it seems to be really random when it does/doesn't work.

---

