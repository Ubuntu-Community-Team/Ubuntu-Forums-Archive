---
title: "no sound ubuntu studio hda via vt82xx"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by evilelviss on 2007-08-29
First time user of linux don't have great knowledge of code and commands and all that!

Have been searching google and google.com/linux with no success for my situation.

The problem is no sound at all, from anything. have tried numerous things such as  alsa mixer(all volume full) front volume also full, ran sound test from sound preferences, tried installing alsa-drivers.

I have noticed that a lot of people are having problems with this type of sound car (maybe because it's cheap and well.... poo!, but it's the best i got)

everything else seems to be running soundly (no pun intended) a few little glitches in gimp such as ghostly windows flashing across the screen every so often but thats it.

I am also having problems trying to get my wireless usb key working, but i'm not too pushed about that at the minute. 

can anybody help me?

here's some stuff :

Ubuntu studio 7.04 "Feisty-fawn" -Release i386

 lspci output from terminal

00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d3 (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

---

### Post by evilelviss on 2007-08-30
lsmod | grep snd
snd_hda_intel          22168  5 
snd_hda_codec         205056  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33408  0 
snd_seq_midi            9600  0 
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            45056  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                80260  5 snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_pcm_oss
snd_timer              24196  3 snd_seq,snd_pcm
snd                    54788  19 snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_rawmidi,snd_seq,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore               9440  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

---

### Post by evilelviss on 2007-08-30
It has been done and i have sound thanks to dirty d

i hope this can help anyone else whom is having the same problem as i was

go here and follow the instructions

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

