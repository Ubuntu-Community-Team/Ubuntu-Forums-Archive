---
title: "Oss Alsa Plug and play!?!"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-03-02
Please could someone help me, as i need my sound. I have:
SIS SI70912 (alsa)
CMI9739 (oss)

ALSA AND OSS??????? - I searched everywhere for an explaination of this, wiki forums etc but found nothing. I thought i only had one soundcard in my machine.

Ive no idea what alsa and oss are but they seem to be conflicting with each other. In ubuntu, i get my system sounds, which seem to be controlled by oss pcm and everything else by alsa pcm.

Also, my recording system doesnt work (although i can hear my voice in the speakers) every application either says 'problem with sound haedware' or /dev/something (dp i think) is in use by another program.

Is there a dpkg-reconfigure thing for sound like there is for Xserver? or
Is there any plug and play capability in linux (except for things like usb)? so i cant get this to work and have to put in the old soundblaster i have kicking around someplace, will i just stick it in and get it set up like in windows?

Please help :-k

---

### Post by mlind on 2006-03-02
[OSS and Alsa]("http://en.wikipedia.org/wiki/ALSA_%28Linux%29") are frameworks that enable you to use your soundcard.
ALSA is newer and preferred option.

I dunno how to resolve conflicts if both soundsystems are loaded at same time,
but you should check [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems).

---

### Post by varunus on 2006-03-02
The reason you see both alsa and oss is because these are two sound systems used by linux.  OSS is the old one, and ALSA is the new one.  Ubuntu's system sounds, and every modern program, should use ALSA to output sound, and you should be fine.

If OSS is controlling your ubuntu sounds, something is wrong...

Lets see a few things.

Open a terminal...can you post the output of "lspci" and "lsmod | grep snd" here?

Also, what happens in a terminal if you type "aplay /usr/share/sounds/phone.wav"?  Do you hear a phone ring?

---

### Post by dgrafix on 2006-03-02
dan@linuxpc:~$ aplay /usr/share/sounds/phone.wav
Playing WAVE '/usr/share/sounds/phone.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Warning: rate is not accurate (requested = 44100Hz, got = 48000Hz)
         please, try the plug plugin (-Dplug:dmixer)
dan@linuxpc:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
dan@linuxpc:~$

---

### Post by dgrafix on 2006-03-02
dan@linuxpc:~$ lsmod | grep snd
snd_intel8x0           30144  8
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  4 snd_pcm_oss
snd_pcm                78344  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  4 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  4 snd



The phone did ring btw. I get some playback in some programs, but usually its intemitttent as if a wire is loose on a speaker , but recording doesnt work at all. Cpu etc is more than capable of playing compressed sounds etc (the pc used to run XP fine).

---

### Post by varunus on 2006-03-03
Hmm...that KHZ error with aplay makes it seem like your sound card is one of the special ones that needs some configuration (mine did too).

Can you give me examples of what programs can play sounds and what can't?  Like, specific examples, and what you have their sound settings set to.  Sorry I'm being vague, but I can't help unless I have a clear picture of what's going on; there are lots of issues that can mess with sound, even just having one rogue app messing with the sound card.

---

### Post by dgrafix on 2006-03-03
if i turned it off in the bios and whacked my soundblaster in, will it get autodetected or is there a prog i run to configure it?

---

### Post by varunus on 2006-03-04
It should get autodetected and just work.

---

### Post by Moonhill on 2006-03-12
I have similar problem with mic and recording. It works but no output. I have p4p800 deluxe onboard sound. Here is my info. What can I do for recording?

kisoo@moonhill:~$ lsmod | grep snd
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm


kisoo@moonhill:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)

---

