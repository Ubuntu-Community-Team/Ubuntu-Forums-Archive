---
title: "Sound installation issues"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by deadcomposers on 2006-04-05
Hi there,

This is my first post and I'm completely new to Linux/Ubuntu so please be nice! I have decided to ditch Windows and discover what Linux has to offer. I intend using Linux mostly for music making, visuals and VJ work. I normally use my Powerbook for music making so I can take my time trying to get things to work with Linux.

I installed Breezy Badger over the weekend on my pc (AMD2000/768Mb). I used the excellent tutorial at [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) to get my Speedtouch modem working but now have a few problems getting sound to work correctly.

I have not currently setup any sound or any additional software with my installation so I have a complete fresh installation.

My main question is what should I do first to get my soundcard (STAudio/Hoontech DSP24) up and running. I am under the impression that I need to install the latest version of ALSA and drivers for my card before I can move forwards. Is this correct?

I've found the driver? at [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Hoontech#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Hoontech#matrix)

I would be really greatful if anyone could explain (in really simple laymans terms!) How to get the latest version of ALSA and the soundcard drivers installed on my system.

Sorry for the long post but thought I'd explain as clearly as possible my situation.

Matt

---

### Post by mlind on 2006-04-05
You should have correct alsa installed by default.

could you give outputs of following commands when you perform those on terminal.
(Applications > Accessories > Terminal)

```

dpkg -l 'alsa*'
lsmod | grep ice1712
cat /proc/asound/cards

```

first command should display at least that alsa-base is installed.
second command should output that ice1712 module is loaded by kernel,
and that sound support is activated for you soundcard.
if 'cat' command shows your STAudio soundcard, then ALSA had recognized it.

Do you head any kind of sound when doing *aplay /usr/share/sounds/phone.wav* ?

If everything above looked okay, launch *alsamixer* from terminal and check that
there's no muted channels.

you need to install some additional stuff from apt repository to get restricted
formats, like mp3's working. See [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by deadcomposers on 2006-04-06
> matthew@ubuntu:~$ dpkg -l 'alsa*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  alsa           <none>         (no description available)
ii  alsa-base      1.0.9b-4       ALSA driver configuration files
un  alsa-oss       <none>         (no description available)
ii  alsa-utils     1.0.9a-4ubuntu ALSA utilities
un  alsalib        <none>         (no description available)
un  alsalib0.1.3   <none>         (no description available)
un  alsalib0.3.0   <none>         (no description available)
un  alsalib0.3.2   <none>         (no description available)
matthew@ubuntu:~$ lsmod | grep ice1712
snd_ice1712            56388  1
snd_ice17xx_ak4xxx      4224  1 snd_ice1712
snd_ak4xxx_adda         6144  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              9216  1 snd_ice1712
snd_ac97_codec         72188  1 snd_ice1712
snd_pcm                78344  3 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_i2c                 5376  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6784  1 snd_ice1712
snd                    48644  14 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device
matthew@ubuntu:~$ cat /proc/asound/cards
0 [DSP24          ]: ICE1712 - Hoontech SoundTrack Audio DSP24
                     Hoontech SoundTrack Audio DSP24 at 0xd400, irq 17


I don't completely understand what this is telling me but everything seems to be recognised. Thanks for the help.

---

### Post by deadcomposers on 2006-04-06
Another sound problem...

When I play an audio CD it sounds really jumpy, as the CD is skipping. Playing the system wav files is fine so it seems the problem baybe a CD setting or CD driver maybe?

---

### Post by deadcomposers on 2006-04-06
I've just installed Automatix which should have corrected my DMA settings, and DVDs play fine through Totem, but audio CDs are still giving me a consistent clicking sound. Any ideas anyone? It's the onlything that is wrong with my installation now.

---

