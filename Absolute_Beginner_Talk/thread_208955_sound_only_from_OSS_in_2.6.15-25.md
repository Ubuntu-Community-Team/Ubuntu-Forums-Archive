---
title: "sound only from OSS in 2.6.15-25"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-07-04
Hi! 

I hear sound only from OSS on 2.6.15-25, and no sound from the others. While I hear sound when I am in 2.6.15-23 kernel, especially from ALSA.

here is what I get when I type **gstreamer-properties**

```
hilal@katara:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'

```

thnx for anyhelp... :)

---

### Post by Kuraboy on 2006-07-06
okay, searched abit more, and tryed to see if the fault is from ALSA.

I checked both this file:

asound.conf:
```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}
```

and when I typed 
```
aplay -l 

```I got
```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and noticed that my Audigy card number is 0 and in the asound.conf it uses the card number 0 right?

so where do I do wrong?

and I also noticed that when I type
```
aslamixer
```
I get the volume controls for the other sound card C-Media which was card number 1... why?!

please, anyone can help?

---

### Post by Happless on 2006-07-08
Kuraboy, 
I have a simmilar problem. On my GA-M51GM-S2G board dapper finds 2 sound devices:

(OSS) Realtek ALC883
(ALSA) HDA Nvidia

now play back seems to work fine, but i would prefer to be using ALSA across the board as at the moment it seems to refuse to use alsa properly for input. Whn i try and play a test sound in the gstramer-properties page i get this error in the terminal:

gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for reading. [gstalsasrc.c(526): gst_alsasrc_open (): /pipeline0/alsasrc1:
Recording open error: Invalid argument]

Other than that I get the same error on mixer start as Kuraboy


as a result i can adjust the alsa mixer properties all I like and it seems to do nothing. Additionally cedga fails when testing alsa. OSS seems to work fine but it just bugs me.

As I am pretty new to this im waaay outta ideas. So Kuraboy, lets hope some one out in the webaverse can save us

---

### Post by Happless on 2006-07-08
Well in the intersets of providing as much info as poss i did much as Kuraboy has.

asound.conf reads:
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}


when i type `aplay -l' i get:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

so now i wonder if its an ALSA support issue or somesuch with my sound chipset

---

### Post by Kuraboy on 2006-07-09
Hi Happless,

it seems that you have only one card?! card 0.
Is there a way to disable the on board sound card that I have? 

and this is wierd, sometimes when I log in OSS works and sometime ALSA works... if ALSA works I hear sound directly from the log in screen, because it is default.. but if OSS works, I need to change it with gstreamer-properties
..

and if lets say OSS works, should ALSA stop working? and vice versa?

weird ^_^;;;

--- update:
I disbale the other sound card, and when I try gstream-properties I get these erroes now
```
hilal@katara:~$ gstreamer-properties
/bin/sh: -c: line 0: unexpected EOF while looking for matching `''
/bin/sh: -c: line 1: syntax error: unexpected end of file
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
OIL: ERROR liboiltest.c 403: oil_test_check_impl(): function merge_linear_u8_sse2 in class merge_linear_u8 failed check (7938 > 0) || (outside=0)
OIL: ERROR liboiltest.c 403: oil_test_check_impl(): function merge_linear_u8_mmx in class merge_linear_u8 failed check (8121 > 0) || (outside=0)
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'

```

I edited pcm "hw:1,0" to pcm "hw0,0" in /etc/asound.conf, now both ALSA and OSS works.. but what about the error message I get from gstream--properties?

thnx

---

### Post by Happless on 2006-07-10
Hrrrmmm...well that is a new wrinkle.

I might try that asound.conf thing and see what i get.

as for disabling your OB sound, go into bios (you know hit del,F2 or whatever) and ok, on my bios i goto:
intergrated peripherals--->onboard audio function---disabled (well i dont as im using OB sound :p )

I shall try the asound thing now (its only 23:50 here after all, and i just finished work ) and post results

EDIT: oops, almost forgot to mention, i got some driver from nVidia for the sound chip. AFAIK it did diddly other than add an alternate mixer, with half the feature the standard. however im gonna check aplay -l `cause thats one thing i forgot to check after those drivers `seemd' to go in :P gotta love nVidia drivers

---

### Post by Happless on 2006-07-10
hmmm...just realised, that both devices appear as being basicly 0,0

as for alsa and oss working together, everything ive read (hey feel free to corrrect me here more knowledgable folk) seems to indicate they should play happilly, at worst with also providding oss emulation for legacy purposes

Now so far i havent noticed much issue. (i am using ubuntu as a base for cedega, and so far im grinnin) in games, or media. Ok i cant have totem running and try play a game. But that seems a bit of a no brainer.

I think I may have to read some more on how the nvidia/realtek deal is setup. I start to suspect that the nVidia chip may be providing raw digital (ALC882 Digital), and the realtech then acting essential as DAC to output to the speaker ports. I have noticed whilst the master volume in the "nvidia" side of the default mixer does....nothing, the front/rear sliders do work. Which kinda lends some extra weight to the 2 chip theory. Whilst writing this, a thought has hit me....I might go check gigabytes page and if nothing else see which chip the winblows drivers support.

TTFN

---

### Post by Happless on 2006-07-10
Weeeeeeeeeeeeeeeeeeeeel!!!

intersting stuff (depending if your as geeky as me) but it seems that the windows drivers provide support for Realtek Azalia audio.

now i have found that realtech have a driver for azalia, but its labled: C-Media Azalia Audio Driver for 915GM-FR & 915PM-ILR only

HUH!?

now it seems people are having some difficulty in general with this chip.

bah...all this is doing my head in. What we both need is for someone who knows wtf is going  on to look at this thread and go hey yeah!

---

