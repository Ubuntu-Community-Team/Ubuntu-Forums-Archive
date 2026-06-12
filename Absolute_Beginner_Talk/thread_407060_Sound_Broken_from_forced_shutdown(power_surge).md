---
title: "Sound Broken from forced shutdown?(power surge)"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-04-11
My computer was shut off due to a power surge. I do have a surge protector, but I have somehow lost the connection to my sound card. around the same time, I updated my system. Is there any way to remove the last updates, or to see if something was accidentally damaged from the surge?

---

### Post by HgBoy on 2007-04-11
[IMG]http://i53.photobucket.com/albums/g47/hgboy/Screenshot.png[/IMG]

This is what my audio settings say. I have tried re-installing the driver, but I keep getting error messages when I try the "make" command. This is my output from the make command.

austin@austin-desktop:~/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26$ make
make dep
make[1]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #3 succeeded at 121 (offset -1 lines).
Hunk #4 succeeded at 133 (offset -1 lines).
Hunk #5 succeeded at 143 (offset -1 lines).
Hunk #6 succeeded at 174 (offset -1 lines).
Hunk #7 succeeded at 506 (offset -1 lines).
Hunk #8 succeeded at 519 (offset -1 lines).
Hunk #9 succeeded at 933 (offset -2 lines).
Hunk #10 succeeded at 980 (offset -2 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #2 succeeded at 2750 (offset 2 lines).
Hunk #3 succeeded at 2770 (offset 2 lines).
Hunk #4 succeeded at 2823 (offset 2 lines).
Hunk #5 succeeded at 2850 (offset 2 lines).
Hunk #6 succeeded at 2941 (offset 2 lines).
Hunk #7 succeeded at 2960 (offset 2 lines).
Hunk #8 succeeded at 2978 (offset 2 lines).
Hunk #9 succeeded at 3007 (offset 2 lines).
Hunk #10 succeeded at 3039 (offset 2 lines).
Hunk #11 succeeded at 3068 (offset 2 lines).
Hunk #12 succeeded at 3097 (offset 2 lines).
Hunk #13 succeeded at 3115 (offset 2 lines).
Hunk #14 succeeded at 3135 (offset 2 lines).
Hunk #15 succeeded at 3151 (offset 2 lines).
Hunk #16 succeeded at 3162 (offset 2 lines).
Hunk #17 succeeded at 3193 (offset 2 lines).
Hunk #18 succeeded at 3257 (offset 2 lines).
Hunk #19 succeeded at 3284 (offset 2 lines).
Hunk #20 succeeded at 3325 (offset 2 lines).
Hunk #21 succeeded at 3468 (offset 2 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #2 succeeded at 1259 (offset 3 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1274 (offset 7 lines).
Hunk #2 succeeded at 1357 (offset 7 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 993 (offset -2 lines).
Hunk #2 succeeded at 1842 (offset 51 lines).
Hunk #3 succeeded at 1896 (offset 51 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #1 succeeded at 2088 (offset 16 lines).
Hunk #2 succeeded at 2254 (offset 16 lines).
Hunk #3 succeeded at 2432 (offset 16 lines).
Hunk #4 succeeded at 2564 (offset 16 lines).
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
make[4]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
make[4]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
make[4]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
Hunk #3 succeeded at 62 with fuzz 1.
Hunk #4 succeeded at 89 with fuzz 2 (offset -58 lines).
Hunk #5 succeeded at 241 (offset -6 lines).
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #1 succeeded at 41 (offset -2 lines).
Hunk #2 succeeded at 753 (offset 4 lines).
Hunk #3 succeeded at 764 (offset 4 lines).
Hunk #4 succeeded at 2883 (offset 70 lines).
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
make[3]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #1 succeeded at 224 (offset -1 lines).
Hunk #2 succeeded at 305 (offset -1 lines).
Hunk #3 succeeded at 331 (offset -1 lines).
make[3]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[2]: Entering directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
make[2]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
make[1]: Leaving directory `/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/hpetimer.o
In file included from /home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/include/adriver.h:677,
                 from /home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/include/sound/driver.h:42,
                 from /home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/hpetimer.c:22:
include/linux/pci.h:496: error: expected identifier or ‘(’ before numeric constant
make[3]: *** [/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/hpetimer.o] Error 1
make[2]: *** [/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore] Error 2
make[1]: *** [_module_/home/austin/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [compile] Error 2
austin@austin-desktop:~/Downloads/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26$

---

### Post by ComplexNumber on 2007-04-11
i would probably bet that its a hardware problem. if i were you, i would have probably checked that theory out first (if you haven't done that already).

recently, my sound started going all funny. i was first alerted to it because the volume applet on my panel showed that the volume was mute. so there's me going "hmmm that looks odd". 
softwarewise, i hadn't changed anything. anyway, i also noticed that my metronome had weird timing. it would skip beats etc. that was even stranger! a software problem could not have caused that.  anyway, it turns out that my sound card wasn't held in properly,and eventually gave way altogether with zero sound. i took the sound card out and put it back in again. problem solved.

---

### Post by HgBoy on 2007-04-11
So, what should I do if my sound card is integrated? Could it be a faulty motherboard or connection? Also, I had similar errors when first installing all of the audio drivers. If I remember correctly, it was just random luck that got it working. I can't even remember what I was changing. The only reason that I thought it was software, was because of the system update I performed just before my system shut down. Is there any way to see *what* I changed?

---

### Post by ComplexNumber on 2007-04-11
> **HgBoy said:**
> So, what should I do if my sound card is integrated? Could it be a faulty motherboard or connection?
maybe. i'm not really a hardware person si couldn't tell you. even though you have an anti-short device, i still don't think having the power switched off like that is going to do the hardware any good.

you recently updated the system? hmmmm that may be a contributor or the cause. best have a look at the hardware first.

---

### Post by HgBoy on 2007-04-12
Took the case apart, everything seems to be fine. Nothing loose, burnt, or otherwise damaged. How can I check which updates I installed, and possibly remove them if necessary to make my sound work?

---

### Post by HgBoy on 2007-04-12
Fixed the issue. Thanks for the help

---

