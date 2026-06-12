---
title: "Sound problem"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by janne5011 on 2005-11-11
Hi. i got one soundcard, and one in my Tv card. the Tv-card have one connector audio-out and cable from that is put in in audio-in, in the first cards connector.
(Sorry my English is bad:)).
I can listen and to to some degrre controll audio from the tvcard for example mute it, but no more :(.the sound from Tv card is on as default but no other audio works.
If I clic on the soundicon there is 2 cards as expected
In system-->sound there is only one card present the first card (not the tvcard)

here is output from lshw:
 *-multimedia:0
             description: Multimedia audio controller
             product: Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:e800-e8ff ioport:ec00-ec7f irq:18
and
*-multimedia:1
             description: Multimedia controller
             product: SAA7134
             vendor: Philips Semiconductors
             physical id: c
             bus info: pci@00:0c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=saa7134
             resources: iomemory:febfa800-febfabff irq:16

here is etc/modules file:

saa7134 card=3 tuner=5 dsp_nr=1 mixer_nr=1 oss=1 oss_rate=32000
aumix -d /dev/mixer1 -1 R

else the Tvcard works as expected.

so..how can I fix sound so I can choose tv or not, and be able to adjust volume and so on:confused:

---

### Post by apjone on 2005-11-11
try preferance's > multimedia system setup

Give that a try 

AJ

---

### Post by janne5011 on 2005-11-11
[QUOTE=apjone]try preferance's > multimedia system setup

Give that a try 

AJ[/QUOTE]

thanks. I tried  but no sucess, the output  from OSS-open sound system was
"testing" but no sound..

---

### Post by apjone on 2005-11-11
have you tried switching between ALSA, OOS and ESD?

---

### Post by janne5011 on 2005-11-11
[QUOTE=apjone]have you tried switching between ALSA, OOS and ESD?[/QUOTE]

yes alsa and esd gives errormessage. "cant construct testpipeline":^o

---

### Post by janne5011 on 2005-11-12
....i found little more info on this with dmesg would be nice if somebody can give me a hint what to try, I have no idea :confused:  
here is the parts of dmesg I guess is relevant

...
[4294692.049000] Linux video capture interface: v1.00
[4294692.210000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4294692.217000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294692.217000] saa7134[0]: found at 0000:00:0c.0, rev: 1, irq: 16, latency: 64, mmio: 0xfebfa800
[4294692.217000] saa7134[0]: subsystem: 1131:0000, board: LifeView FlyVIDEO2000 [card=3,insmod option]
[4294692.217000] saa7134[0]: board init: gpio is 80407f
[4294692.217000] saa7134[0]: there are different flyvideo cards with different tuners
[4294692.217000] saa7134[0]: out there, you might have to use the tuner=<nr> insmod
[4294692.217000] saa7134[0]: option to override the default value.
[4294692.218000] saa7134[0]: registered input device for IR
[4294692.322000] saa7134[0]: Huh, no eeprom present (err=-5)?
[4294692.333000] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[4294692.333000] tuner 0-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[4294692.337000] saa7134[0]: registered device video0 [v4l2]
[4294692.337000] saa7134[0]: registered device vbi0
[4294692.367000] saa7134[0]: registered device radio0
[4294692.368000] saa7134[0]: registered device dsp1
[4294692.368000] saa7134[0]: registered device mixer1
[4294695.207000] saa7134[0]/audio: audio carrier scan failed, using 5.500 MHz [default]
[default]
...
[4294698.508000] AC'97 0 analog subsections not ready
[4294698.568000] intel8x0_measure_ac97_clock: measured 49458 usecs
[4294698.568000] intel8x0: clocking to 48000
[4294701.206000] Real Time Clock Driver v1.12
[4294701.289000] input: PC Speaker

---

