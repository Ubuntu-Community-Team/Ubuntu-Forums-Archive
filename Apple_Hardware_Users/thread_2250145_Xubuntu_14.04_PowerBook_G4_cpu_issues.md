---
title: "Xubuntu 14.04 PowerBook G4 cpu issues"
date: 2014-10-27
forum: Apple Hardware Users
---

### Post by rican-linux on 2014-10-27
I just installed Xubuntu on my PowerBook G4 and uprgaded to 14.04. After fixing sound and video card issues I am asking to see if anyone has had any issue with cpu performance. When ever I watch video like youtube it peaks at 100% and becomes very slow. I know this hardware is almost 10 years old bbut I was hoping for a little better performance. Any help would be appreciated.

laptop:~$ uname -a
Linux laptop 3.13.0-37-powerpc-smp #64-Ubuntu SMP Mon Sep 22 21:30:13 UTC 2014 ppc ppc ppc GNU/Linux
laptop:~$ cat /proc/cpuinfo 
processor	: 0
cpu		: 7447A, altivec supported
clock		: 1666.666000MHz
revision	: 1.2 (pvr 8003 0102)
bogomips	: 36.86

total bogomips	: 36.86
timebase	: 18432000
platform	: PowerMac
model		: PowerBook5,6
machine		: PowerBook5,6
motherboard	: PowerBook5,6 MacRISC3 Power Macintosh 
detected as	: 287 (PowerBook G4 15")
pmac flags	: 0000001b
L2 cache	: 512K unified
pmac-generation	: NewWorld
Memory		: 2048 MB
laptop:~$

---

### Post by lukeiamyourfather on 2014-10-27
Most videos online including those on YouTube are encoded with H.264 which requires a lot of calculations to decode. Modern hardware relies on the GPU to decode H.264 videos because it would otherwise be a significant load on the CPU. For example, AMD's decoder that uses the GPU.

[http://en.wikipedia.org/wiki/Unified_Video_Decoder](http://en.wikipedia.org/wiki/Unified_Video_Decoder)

Your hardware predates the GPU decoders so it must use the CPU to decode the video which is a lot to ask of a processor circa 2002, probably not the answer you're looking for. Sorry!

---

### Post by rican-linux on 2014-10-27
It is not what I wanted to  hear. I am also noticing that launch an app or sometimes at random the CPU will spike to 96-100% the culprit is usr/bin/X. I want to know is Xorg just too intensive for a PowerMac even using XFCE as the desktop?

---

### Post by dr.david.maloney on 2014-10-27
Step one:

sudo apt-get install LXDE. XFCE is not what it used to be. Alternatively install Windowmaker, but that is a windowing environment rather than a true desktop. LXDE should be fine for a Powerbook with those specs.

Step two: 

Since you have no hated and awful Adobe Flash to avoid, you must simply make the most out of what you have. Read:

[http://ppcluddite.blogspot.com/2013/01/some-cross-platform-flash-alternatives.html](http://ppcluddite.blogspot.com/2013/01/some-cross-platform-flash-alternatives.html)

[http://ppcluddite.blogspot.com/2011/05/hd-on-old-mac-with-mplayer.html](http://ppcluddite.blogspot.com/2011/05/hd-on-old-mac-with-mplayer.html)

Second link is refering to OS X, but most of those commands and arguements work (with adjustments, like you type mplayer at the prompt instead of  /Applications/mplayer of course) for mplayer and Linux.

Also:

Download files in Iceweseal Firefox and play them back instead of stream them. Or:

Copy the url link in Iceweasel or Firefox with download helper extension and paste the url into VLC or gnomeMplayer. Quit the browser. Enjoy the video.

Have you installed restricted extras and extra codecs? 

If you don't have minitube, install it. Set to 360p. Enjoy a little pixlelation with your video. 

Consider plain jain Debian or, LubuntuPPC or MintPPC. Install compton for some transparency and Docky. Or, Ubuntu 12.04 LTS with Unity 2D.

---

### Post by dand1972 on 2014-10-28
I didn't see whether you said you were streaming Youtube in standard or hi-def.  Your cpu is plenty fast enough to stream standard def mp4s, so the problem is your system (I can stream standard def on a G3 iBook).  Maybe your 2D acceleration isn't working.  I'm with the above poster who said you should try 12.04 LTS.  It's older radeon drivers will give you much better video support.

---

### Post by rican-linux on 2014-10-28
LXDE is working fine and streaming with mpv works great! No slowness at all. However when I went the Linux Action Show page and downloaded their current mp4 episode It was much slower playing on my desktop than streaming. I would think it would be faster.

I have concerns going with Debian. In the past getting it configured was just a pain and I am not sure if it trying it again will be any better. I will try going Ubuntu 12.04 LTS and let you all how it goes.

---

### Post by rican-linux on 2014-10-28
I just installed ubuntu 14.04. Right now my sound is not working. I had the same issue when nI upgraded to Xubuntu 14.04 and the fix was to blacklist snd-powermac and the snd-aoa modules to /etc/modules. However when I did that here it is still not working. I do not even think it is seeing my speakers. see below

linuxppc-laptop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.24.
linuxppc-laptop:~$ cat /proc/asound/modules 
 0 snd_aoa_fabric_layout
linuxppc-laptop:~$ cat /proc/asound/devices 
  1:        : sequencer
  2: [ 0]   : control
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
 33:        : timer
linuxppc-laptop:~$ cat /proc/asound/cards
 0 [SoundByLayout  ]: AppleOnbdAudio - SoundByLayout
                      SoundByLayout
linuxppc-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#snd_powermac
apm_emu
#snd-powermac
therm_adt746x
snd-aoa-i2sbus
snd-aoa-fabric-layout
snd-aoa-codec-tas
snd-aoa-codec-onyx
snd-aoa-soundbus
snd-aoa
snd_aoa
snd_aoa_soundbus
snd_aoa_codec_tas
snd_aoa_codec_onyx
snd_aoa_fabric_layout
snd_aoa_i2sbus
linuxppc-laptopt$

---

### Post by rican-linux on 2014-10-29
here is more info

rican-linux@linuxppc-laptop:~$ cat /proc/asound/oss/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.24 emulation code)
Kernel: Linux linuxppc-laptop 3.2.0-70-powerpc-smp #105-Ubuntu SMP Wed Sep 24 19:51:38 UTC 2014 ppc
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
SoundByLayout

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG
rican-linux@linuxppc-laptop:~$ 

syslog

Oct 28 19:11:59 linuxppc-laptop kernel: [    0.026363] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 19:11:59 linuxppc-laptop kernel: [    0.026378]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 19:11:59 linuxppc-laptop kernel: [    0.026394]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 19:11:59 linuxppc-laptop kernel: [    0.026482] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 19:11:59 linuxppc-laptop kernel: [    0.026494]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 19:11:59 linuxppc-laptop kernel: [    0.026515] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 19:11:59 linuxppc-laptop kernel: [    0.037042] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 19:11:59 linuxppc-laptop kernel: [    0.037050] i2c-core: driver [aat2870] using legacy resume method
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799547] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799552] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799558] PowerMac i2c bus pmu 2 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799626] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799631] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799636] PowerMac i2c bus pmu 1 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799691] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799696] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799700] PowerMac i2c bus mac-io 0 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799764] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799769] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799774] PowerMac i2c bus uni-n 0 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799837] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.799842] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [    1.804515] PowerMac i2c bus uni-n 1 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.026370] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.026385]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.026401]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.026491] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.026503]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.026524] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.037048] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 19:37:41 linuxppc-laptop kernel: [    0.037057] i2c-core: driver [aat2870] using legacy resume method
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803574] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803579] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803584] PowerMac i2c bus pmu 2 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803652] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803657] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803662] PowerMac i2c bus pmu 1 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803717] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803722] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803726] PowerMac i2c bus mac-io 0 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803791] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803795] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803801] PowerMac i2c bus uni-n 0 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803864] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.803869] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [    1.808606] PowerMac i2c bus uni-n 1 registered
Oct 28 19:43:52 linuxppc-laptop kernel: [    0.026365] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 19:43:52 linuxppc-laptop kernel: [    0.026380]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 19:43:52 linuxppc-laptop kernel: [    0.026396]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 19:43:52 linuxppc-laptop kernel: [    0.026484] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 19:43:52 linuxppc-laptop kernel: [    0.026497]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 19:43:52 linuxppc-laptop kernel: [    0.026517] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 19:43:53 linuxppc-laptop kernel: [    0.037056] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 19:43:53 linuxppc-laptop kernel: [    0.037064] i2c-core: driver [aat2870] using legacy resume method
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799559] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799564] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799570] PowerMac i2c bus pmu 2 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799638] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799643] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799648] PowerMac i2c bus pmu 1 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799703] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799708] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799712] PowerMac i2c bus mac-io 0 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799777] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799782] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799788] PowerMac i2c bus uni-n 0 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799853] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.799858] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [    1.804546] PowerMac i2c bus uni-n 1 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.264635] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.264645] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.264653] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.264658] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.264663] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.264668] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.334778] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.334805] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.334809] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.334820] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.334896] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379342] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379353] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379364] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379369] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379375] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379379] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379387] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379392] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379399] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [   20.379404] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.026367] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.026382]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.026399]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.026488] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.026500]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.026520] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.037054] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 20:00:52 linuxppc-laptop kernel: [    0.037062] i2c-core: driver [aat2870] using legacy resume method
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803590] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803595] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803601] PowerMac i2c bus pmu 2 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803669] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803674] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803679] PowerMac i2c bus pmu 1 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803735] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803740] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803744] PowerMac i2c bus mac-io 0 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803808] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803813] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803819] PowerMac i2c bus uni-n 0 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803882] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.803887] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [    1.808617] PowerMac i2c bus uni-n 1 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.125720] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.125730] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.125739] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.125743] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.125749] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.125753] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.190686] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.190713] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.190718] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.190727] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.190732] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227830] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227841] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227851] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227856] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227862] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227866] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227874] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227879] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227887] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [   20.227891] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.026363] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.026378]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.026394]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.026485] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.026497]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.026518] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.037059] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 20:04:44 linuxppc-laptop kernel: [    0.037068] i2c-core: driver [aat2870] using legacy resume method
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799567] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799573] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799578] PowerMac i2c bus pmu 2 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799647] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799652] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799656] PowerMac i2c bus pmu 1 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799711] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799716] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799721] PowerMac i2c bus mac-io 0 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799785] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799790] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799796] PowerMac i2c bus uni-n 0 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799860] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.799865] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [    1.804558] PowerMac i2c bus uni-n 1 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.282943] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.282956] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.282965] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.282969] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.282975] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.282980] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.360287] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.360314] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.360319] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.360329] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.360334] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410073] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410086] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410098] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410102] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410108] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410113] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410121] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410125] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410133] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [   20.410138] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.026353] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.026368]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.026385]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.026474] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.026487]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.026508] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.037050] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 20:20:47 linuxppc-laptop kernel: [    0.037058] i2c-core: driver [aat2870] using legacy resume method
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799558] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799563] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799569] PowerMac i2c bus pmu 2 registered
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799636] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799641] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799646] PowerMac i2c bus pmu 1 registered
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799701] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799706] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799710] PowerMac i2c bus mac-io 0 registered
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799774] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799779] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799784] PowerMac i2c bus uni-n 0 registered
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799848] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.799853] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [    1.804538] PowerMac i2c bus uni-n 1 registered
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.351027] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.351037] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.351045] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.351049] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.351055] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.351059] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.418776] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.418802] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.418807] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.418818] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.418889] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479669] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479679] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479690] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479695] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479701] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479706] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479714] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479718] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479726] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:20:47 linuxppc-laptop kernel: [   20.479731] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.026375] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.026390]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.026407]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.026494] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.026506]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.026527] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.037055] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 20:50:41 linuxppc-laptop kernel: [    0.037064] i2c-core: driver [aat2870] using legacy resume method
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803582] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803587] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803593] PowerMac i2c bus pmu 2 registered
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803661] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803666] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803671] PowerMac i2c bus pmu 1 registered
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803726] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803731] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803735] PowerMac i2c bus mac-io 0 registered
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803800] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803805] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803810] PowerMac i2c bus uni-n 0 registered
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803874] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.803879] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [    1.808616] PowerMac i2c bus uni-n 1 registered
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.451734] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.451743] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.451751] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.451756] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.451761] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.451766] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.530178] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.530206] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.530210] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.530220] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.530225] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583351] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583361] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583372] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583376] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583382] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583387] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583395] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583399] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583407] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:50:41 linuxppc-laptop kernel: [   20.583411] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.026345] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.026360]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.026377]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.026467] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.026479]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.026499] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.037036] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 21:02:15 linuxppc-laptop kernel: [    0.037045] i2c-core: driver [aat2870] using legacy resume method
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799545] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799551] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799556] PowerMac i2c bus pmu 2 registered
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799623] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799628] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799633] PowerMac i2c bus pmu 1 registered
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799689] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799694] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799698] PowerMac i2c bus mac-io 0 registered
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799762] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799767] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799773] PowerMac i2c bus uni-n 0 registered
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799836] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.799841] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [    1.804532] PowerMac i2c bus uni-n 1 registered
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.286791] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.286801] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.286881] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.286886] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.286892] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.286896] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.356411] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.356438] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.356443] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.356453] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.356457] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411911] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411922] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411933] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411937] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411944] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411948] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411956] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411961] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411968] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 21:02:16 linuxppc-laptop kernel: [   20.411973] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.026362] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.026377]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.026393]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.026483] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.026495]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.026515] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.037054] i2c-core: driver [aat2870] using legacy suspend method
Oct 29 09:02:58 linuxppc-laptop kernel: [    0.037062] i2c-core: driver [aat2870] using legacy resume method
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799558] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799564] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799569] PowerMac i2c bus pmu 2 registered
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799637] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799641] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799646] PowerMac i2c bus pmu 1 registered
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799701] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799705] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799710] PowerMac i2c bus mac-io 0 registered
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799774] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799779] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799785] PowerMac i2c bus uni-n 0 registered
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799849] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.799854] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [    1.804540] PowerMac i2c bus uni-n 1 registered
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.360179] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.360192] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.360201] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.360205] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.360211] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.360215] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.426645] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.426672] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.426677] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.426687] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.426692] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468738] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468748] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468761] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468765] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468771] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468776] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468784] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468789] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468797] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:02:58 linuxppc-laptop kernel: [   20.468801] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221571] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221584] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221595] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221600] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221606] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221611] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221619] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221624] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221631] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 09:08:02 linuxppc-laptop kernel: [  325.221636] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.026242] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.026257]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.026273]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.026363] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.026375]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.026396] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.036866] i2c-core: driver [aat2870] using legacy suspend method
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.036875] i2c-core: driver [aat2870] using legacy resume method
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.731844] i2c i2c-2: unable to read EDID block.
Oct 29 10:11:43 linuxppc-laptop kernel: [    0.883872] i2c i2c-2: unable to read EDID block.
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.035896] i2c i2c-2: unable to read EDID block.
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452439] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452445] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452451] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452456] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452461] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452466] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452471] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    1.452476] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751368] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751373] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751378] PowerMac i2c bus pmu 2 registered
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751445] i2c i2c-5: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751450] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751454] PowerMac i2c bus pmu 1 registered
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751510] i2c i2c-6: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751515] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751519] PowerMac i2c bus mac-io 0 registered
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751574] i2c i2c-7: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751579] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751585] PowerMac i2c bus uni-n 0 registered
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751657] i2c i2c-8: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.751663] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [    2.756406] PowerMac i2c bus uni-n 1 registered
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399476] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399484] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399491] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399496] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399501] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399505] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399511] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399515] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399521] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399525] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399532] i2c i2c-5: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399537] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399542] i2c i2c-6: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399547] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399643] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399654] i2c i2c-7: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399659] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399666] i2c i2c-8: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   20.399671] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230561] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230570] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230576] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230581] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230586] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230591] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230596] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230601] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230606] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230611] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230620] i2c i2c-5: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230624] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230630] i2c i2c-6: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230635] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230670] i2c i2c-7: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230675] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230683] i2c i2c-8: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:11:43 linuxppc-laptop kernel: [   21.230687] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516623] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516636] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516644] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516648] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516654] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516659] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516664] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516669] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516674] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516679] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516689] i2c i2c-5: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516693] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516699] i2c i2c-6: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516704] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516712] i2c i2c-7: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516717] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516724] i2c i2c-8: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:20:23 linuxppc-laptop kernel: [  541.516729] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848712] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848725] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848734] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848739] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848744] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848749] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848754] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848759] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848765] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848769] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848779] i2c i2c-5: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848784] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848790] i2c i2c-6: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848794] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848802] i2c i2c-7: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848807] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848815] i2c i2c-8: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:33:01 linuxppc-laptop kernel: [ 1299.848820] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.026239] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.026254]  channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.026270]  channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.026361] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.026374]  channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.026395] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.036885] i2c-core: driver [aat2870] using legacy suspend method
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.036893] i2c-core: driver [aat2870] using legacy resume method
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.731979] i2c i2c-2: unable to read EDID block.
Oct 29 10:44:14 linuxppc-laptop kernel: [    0.884021] i2c i2c-2: unable to read EDID block.
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.036019] i2c i2c-2: unable to read EDID block.
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452460] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452466] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452472] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452476] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452481] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452486] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452491] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    1.452496] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751397] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751403] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751409] PowerMac i2c bus pmu 2 registered
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751474] i2c i2c-5: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751479] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751484] PowerMac i2c bus pmu 1 registered
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751540] i2c i2c-6: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751545] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751549] PowerMac i2c bus mac-io 0 registered
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751603] i2c i2c-7: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751608] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751614] PowerMac i2c bus uni-n 0 registered
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751687] i2c i2c-8: therm_adt746x: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.751692] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [    2.756434] PowerMac i2c bus uni-n 1 registered
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669321] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669332] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669339] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669343] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669349] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669353] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669359] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669363] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669369] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669373] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669380] i2c i2c-5: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669385] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669390] i2c i2c-6: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.669395] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.673347] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.673371] i2c i2c-7: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.673377] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.673387] i2c i2c-8: aoa_codec_tas: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.673391] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696139] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696151] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696159] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696163] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696169] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696173] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696179] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696183] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696189] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696193] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696203] i2c i2c-5: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696207] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696213] i2c i2c-6: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696218] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696225] i2c i2c-7: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696230] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696237] i2c i2c-8: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 10:44:14 linuxppc-laptop kernel: [   25.696242] i2c i2c-8: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.842972] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.842985] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.842993] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.842997] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843003] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843008] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843013] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843018] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843024] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843028] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843038] i2c i2c-5: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843042] i2c i2c-5: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843048] i2c i2c-6: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843053] i2c i2c-6: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843061] i2c i2c-7: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843066] i2c i2c-7: Please use another way to instantiate your i2c_client
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843073] i2c i2c-8: aoa_codec_onyx: attach_adapter method is deprecated
Oct 29 13:42:55 linuxppc-laptop kernel: [10747.843078] i2c i2c-8: Please use another way to instantiate your i2c_client

---

### Post by rican-linux on 2014-10-29
moving this to anther thread since this is a new issue.

---

