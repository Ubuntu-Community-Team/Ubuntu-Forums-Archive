---
title: "OSS Emulation Broken"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by lgvier on 2005-10-14
Hi!

I had uninstalled alsa-base and alsa-utils in the past...
Now, I reinstalled alsa-utils and discover (since alsa-base is deprecated)
Alsa works fine, but OSS-Emulation no, the file /dev/dsp* does not exist..
I created a file called "alsa" in /etc/modprobe.d (content above), but this not solve the problem...

Can anyone help me?

This is my /etc/modprobe.d file:
 This sets up the ALSA and OSS portion
alias char-major-116 snd
alias char-major-14 soundcore

# Replace "driver" with the driver for you soundcard
alias snd-card-0 snd-driver
alias sound-slot-0 snd-card-0

# Configure the OSS emulation layer
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

# If you have more than 1 card, set this number to the correct value
options snd cards_limit=1
options snd-pcm-oss nonblock_open=1



---------------------------------------
This is the result of cat /dev/sndstat:

oot@fr0g:~ # cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux fr0g 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
ESS ES1978 (Maestro 2E) at 0x4400, irq 11

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ESS ES1978 (Maestro 2E) MIDI

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG

---

