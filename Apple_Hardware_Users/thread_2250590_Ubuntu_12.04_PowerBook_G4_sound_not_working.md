---
title: "Ubuntu 12.04 PowerBook G4 sound not working"
date: 2014-10-29
forum: Apple Hardware Users
---

### Post by rican-linux on 2014-10-29
I just migrated my PowerBook G4 from Xubuntu 14.04 to Ubuntu 12.02. NOw that I have done so my sound is not working at all. I have updated my /etc/modules file and rebooted but still nothing.any help will be muchh appreciated.

laptop:~$ uname -a
Linux laptop 3.13.0-37-powerpc-smp #64-Ubuntu SMP Mon Sep 22 21:30:13 UTC 2014 ppc ppc ppc GNU/Linux
laptop:~$ cat /proc/cpuinfo
processor : 0
cpu : 7447A, altivec supported
clock : 1666.666000MHz
revision : 1.2 (pvr 8003 0102)
bogomips : 36.86

total bogomips : 36.86
timebase : 18432000
platform : PowerMac
model : PowerBook5,6
machine : PowerBook5,6
motherboard : PowerBook5,6 MacRISC3 Power Macintosh
detected as : 287 (PowerBook G4 15")
pmac flags : 0000001b
L2 cache : 512K unified
pmac-generation : NewWorld
Memory : 2048 MB
laptop:~$ 

linuxppc-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
linuxppc-laptop:~$ cat /proc/asound/modules
0 snd_aoa_fabric_layout
linuxppc-laptop:~$ cat /proc/asound/devices
1: : sequencer
2: [ 0] : control
3: [ 0- 0]: digital audio playback
4: [ 0- 0]: digital audio capture
33: : timer
linuxppc-laptop:~$ cat /proc/asound/cards
0 [SoundByLayout ]: AppleOnbdAudio - SoundByLayout
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
snd_aoa_codec_tas
snd_aoa_codec_onyx
snd_aoa_fabric_layout
snd_aoa_i2sbus

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

Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.026363] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.026378] channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.026394] channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.026482] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.026494] channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.026515] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.037042] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 19:11:59 linuxppc-laptop kernel: [ 0.037050] i2c-core: driver [aat2870] using legacy resume method
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799547] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799552] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799558] PowerMac i2c bus pmu 2 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799626] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799631] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799636] PowerMac i2c bus pmu 1 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799691] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799696] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799700] PowerMac i2c bus mac-io 0 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799764] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799769] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799774] PowerMac i2c bus uni-n 0 registered
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799837] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.799842] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:11:59 linuxppc-laptop kernel: [ 1.804515] PowerMac i2c bus uni-n 1 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.026370] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.026385] channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.026401] channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.026491] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.026503] channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.026524] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.037048] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 19:37:41 linuxppc-laptop kernel: [ 0.037057] i2c-core: driver [aat2870] using legacy resume method
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803574] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803579] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803584] PowerMac i2c bus pmu 2 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803652] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803657] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803662] PowerMac i2c bus pmu 1 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803717] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803722] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803726] PowerMac i2c bus mac-io 0 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803791] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803795] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803801] PowerMac i2c bus uni-n 0 registered
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803864] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.803869] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:37:41 linuxppc-laptop kernel: [ 1.808606] PowerMac i2c bus uni-n 1 registered
Oct 28 19:43:52 linuxppc-laptop kernel: [ 0.026365] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 19:43:52 linuxppc-laptop kernel: [ 0.026380] channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 19:43:52 linuxppc-laptop kernel: [ 0.026396] channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 19:43:52 linuxppc-laptop kernel: [ 0.026484] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 19:43:52 linuxppc-laptop kernel: [ 0.026497] channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 19:43:52 linuxppc-laptop kernel: [ 0.026517] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 19:43:53 linuxppc-laptop kernel: [ 0.037056] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 19:43:53 linuxppc-laptop kernel: [ 0.037064] i2c-core: driver [aat2870] using legacy resume method
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799559] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799564] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799570] PowerMac i2c bus pmu 2 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799638] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799643] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799648] PowerMac i2c bus pmu 1 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799703] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799708] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799712] PowerMac i2c bus mac-io 0 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799777] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799782] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799788] PowerMac i2c bus uni-n 0 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799853] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.799858] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 1.804546] PowerMac i2c bus uni-n 1 registered
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.264635] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.264645] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.264653] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.264658] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.264663] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.264668] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.334778] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.334805] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.334809] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.334820] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.334896] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379342] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379353] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379364] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379369] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379375] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379379] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379387] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379392] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379399] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 19:43:53 linuxppc-laptop kernel: [ 20.379404] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.026367] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.026382] channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.026399] channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.026488] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.026500] channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.026520] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.037054] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 20:00:52 linuxppc-laptop kernel: [ 0.037062] i2c-core: driver [aat2870] using legacy resume method
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803590] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803595] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803601] PowerMac i2c bus pmu 2 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803669] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803674] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803679] PowerMac i2c bus pmu 1 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803735] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803740] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803744] PowerMac i2c bus mac-io 0 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803808] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803813] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803819] PowerMac i2c bus uni-n 0 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803882] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.803887] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 1.808617] PowerMac i2c bus uni-n 1 registered
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.125720] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.125730] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.125739] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.125743] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.125749] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.125753] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.190686] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.190713] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.190718] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.190727] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.190732] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227830] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227841] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227851] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227856] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227862] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227866] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227874] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227879] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227887] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:00:52 linuxppc-laptop kernel: [ 20.227891] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.026363] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.026378] channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.026394] channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.026485] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.026497] channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.026518] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.037059] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 20:04:44 linuxppc-laptop kernel: [ 0.037068] i2c-core: driver [aat2870] using legacy resume method
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799567] i2c i2c-0: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799573] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799578] PowerMac i2c bus pmu 2 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799647] i2c i2c-1: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799652] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799656] PowerMac i2c bus pmu 1 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799711] i2c i2c-2: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799716] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799721] PowerMac i2c bus mac-io 0 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799785] i2c i2c-3: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799790] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799796] PowerMac i2c bus uni-n 0 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799860] i2c i2c-4: therm_adt746x: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.799865] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 1.804558] PowerMac i2c bus uni-n 1 registered
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.282943] i2c i2c-0: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.282956] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.282965] i2c i2c-1: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.282969] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.282975] i2c i2c-2: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.282980] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.360287] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0/codec@6a
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.360314] i2c i2c-3: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.360319] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.360329] i2c i2c-4: aoa_codec_tas: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.360334] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410073] i2c i2c-0: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410086] i2c i2c-0: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410098] i2c i2c-1: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410102] i2c i2c-1: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410108] i2c i2c-2: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410113] i2c i2c-2: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410121] i2c i2c-3: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410125] i2c i2c-3: Please use another way to instantiate your i2c_client
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410133] i2c i2c-4: aoa_codec_onyx: attach_adapter method is deprecated
Oct 28 20:04:44 linuxppc-laptop kernel: [ 20.410138] i2c i2c-4: Please use another way to instantiate your i2c_client
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.026353] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.026368] channel 1 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@1
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.026385] channel 0 bus /uni-n@f8000000/i2c@f8001000/i2c-bus@0
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.026474] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.026487] channel 0 bus /pci@f2000000/mac-io@17/i2c@18000/i2c-bus@0
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.026508] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.037050] i2c-core: driver [aat2870] using legacy suspend method
Oct 28 20:20:47 linuxppc-laptop kernel: [ 0.037058] i2c-core: driver [aat2870] using legacy resume method

---

### Post by rican-linux on 2014-10-29
I found the issue I need to set the PCM channel to 80 in alsamixer. I should have the Ubuntu Wiki more closely the first paragraph under "Why do In have no sound?" mentioned it.

---

