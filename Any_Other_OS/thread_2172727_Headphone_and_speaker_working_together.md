---
title: "Headphone and speaker working together"
date: 2013-09-06
forum: Any Other OS
---

### Post by hectorsales on 2013-09-06
Hi I have the following problem, when I plug headphones into the front panel of my desktop PC speakers are not muted . My OS is Linux Mint 13 Mate 64 bytes (based on ubuntu 12.04).


**Card type**


```
cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbbf4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfbdfc000 irq 19

```

**Card model**


```
cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

```

**Chip and codec**


```
cat /proc/asound/card0/codec#0 | grep Code
Codec: VIA VT1708S

```

According to the information on this page for the model VIA Chip (VIA VT17xx/VT18xx/VT20xx) should put the following to the file** gksudo pluma /etc/modprobe.d /alsa-base.conf**


**options snd-hda-intel** [COLOR=#ff0000]model=auto[/COLOR]


[https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)


I tried other options:


**options snd-hda-intel model=auto**
**options snd-hda-intel model=auto probe_mask=0x103**
**options snd-hda-intel model=auto probe_mask=0x103 enable_msi=0**
**options snd-hda-intel model=auto probe_mask=0x103 position_fix=1**


But unfortunately none of them work...:frown:.

Any suggestions, ideas will be well received ....;)

---

