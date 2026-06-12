---
title: "MacPro sound was perfect now nothing"
date: 2009-12-26
forum: Apple Hardware Users
---

### Post by fatum on 2009-12-26
I installed 9.10 in the beginning of the month with everything working on my MacPro Dual Quad 2.83ghz. It was the smoothest install ever for me with Linux. Now we are 26 days later and sound is not working. These are my outputs from a couple commands that I found for debugging sound 

```

sudo aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

```

lspci -v | less

0:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at 90b04000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```

And my user log file is going crazy with pulseaudio here is a snippet. 

```

Dec 26 11:58:00 UbuntuPro pulseaudio[3056]: ratelimit.c: 3 events suppressed
Dec 26 12:01:14 UbuntuPro pulseaudio[5254]: pid.c: Daemon already running.
Dec 26 12:01:14 UbuntuPro pulseaudio[5255]: pid.c: Daemon already running.
Dec 26 12:01:22 UbuntuPro pulseaudio[5249]: ratelimit.c: 16 events suppressed
Dec 26 12:02:37 UbuntuPro pulseaudio[5249]: ratelimit.c: 129 events suppressed
Dec 26 12:05:29 UbuntuPro pulseaudio[5249]: ratelimit.c: 79 events suppressed
Dec 26 12:13:52 UbuntuPro pulseaudio[5249]: ratelimit.c: 86 events suppressed
Dec 26 12:16:44 UbuntuPro pulseaudio[5527]: pid.c: Daemon already running.
Dec 26 12:17:12 UbuntuPro pulseaudio[5523]: ratelimit.c: 7 events suppressed
Dec 26 12:17:31 UbuntuPro pulseaudio[5523]: ratelimit.c: 127 events suppressed
Dec 26 12:32:35 UbuntuPro pulseaudio[5523]: ratelimit.c: 254 events suppressed
Dec 26 12:32:55 UbuntuPro pulseaudio[5523]: ratelimit.c: 31 events suppressed
Dec 26 12:33:21 UbuntuPro pulseaudio[5523]: module.c: Failed to open module "module-raop-discover": file not found
Dec 26 12:33:21 UbuntuPro pulseaudio[5523]: module-gconf.c: pa_module_load() failed
Dec 26 12:34:39 UbuntuPro pulseaudio[5523]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Dec 26 12:34:39 UbuntuPro pulseaudio[5523]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Dec 26 12:34:39 UbuntuPro pulseaudio[5523]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Dec 26 12:42:27 UbuntuPro pulseaudio[2931]: module.c: Failed to open module "module-raop-discover": file not found
Dec 26 12:42:27 UbuntuPro pulseaudio[2931]: module-gconf.c: pa_module_load() failed

```

as you can see there is a part in there "Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers." which I have sent my output to them through a command in terminal. 

What I am not understanding is why audio is not working anymore. It worked for 25 days with no issues and now nothing. I am very confused can anyone please shed some light on why this could be happening? 

Before anyone asks there is nothing being muted in sound preferences, all the levels are at 100% and my card is seen and selected in sound preferences. If I connect to my bluetooth headset I get audio but it studders every couple seconds with the user.log showing 

```

Dec 25 21:38:38 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 34991 us (= 6172 bytes) in audio stream
Dec 25 21:38:38 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 47766 us (= 8424 bytes) in audio stream
Dec 25 21:38:39 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 50742 us (= 8948 bytes) in audio stream
Dec 25 21:38:39 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 17812 us (= 3140 bytes) in audio stream
Dec 25 21:38:40 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 66741 us (= 11772 bytes) in audio stream
Dec 25 21:38:40 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 44518 us (= 7852 bytes) in audio stream
Dec 25 21:38:40 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 7787 us (= 1372 bytes) in audio stream
Dec 25 21:38:41 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 19948 us (= 3516 bytes) in audio stream
Dec 25 21:38:41 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 52844 us (= 9320 bytes) in audio stream
Dec 25 21:38:41 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 38697 us (= 6824 bytes) in audio stream
Dec 25 21:38:41 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 29801 us (= 5256 bytes) in audio stream
Dec 25 21:38:42 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 40981 us (= 7228 bytes) in audio stream
Dec 25 21:38:42 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 37787 us (= 6664 bytes) in audio stream
Dec 25 21:38:43 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 48726 us (= 8592 bytes) in audio stream
Dec 25 21:38:43 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 14794 us (= 2608 bytes) in audio stream
Dec 25 21:38:43 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 40738 us (= 7184 bytes) in audio stream
Dec 25 21:38:43 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 17814 us (= 3140 bytes) in audio stream
Dec 25 21:38:44 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 12947 us (= 2280 bytes) in audio stream
Dec 25 21:38:44 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 59806 us (= 10548 bytes) in audio stream
Dec 25 21:38:45 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 8997 us (= 1584 bytes) in audio stream
Dec 25 21:38:45 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 61777 us (= 10896 bytes) in audio stream
Dec 25 21:38:45 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 770 us (= 132 bytes) in audio stream
Dec 25 21:38:45 UbuntuPro pulseaudio[10447]: module-bluetooth-device.c: Skipping 38532 us (= 6796 bytes) in audio stream
Dec 25 21:39:02 UbuntuPro pulseaudio[10447]: ratelimit.c: 132 events suppressed

```

Any help would be appreciated. Thank you

---

### Post by fatum on 2009-12-27
I signed into my room mates account on the same machine and there was still no sound which tells me it is a system wide failure not just a config problem on my end. I uninstalled pulseaudio and reinstalled and it did not fix the issue, yet. Uninstalling and reinstalling did fix the issue but I needed a restart between each step. So to fix my disappearing sound issue I the following worked for now. 

1. Uninstall Pulseaudio, I did this through Synaptic
2. Restart the computer
3. Reinstall Pulseaudio
4. Restart the computer
5. Go to sound preferences in System> Preferences> Sound and make sure the sound card is selected correctly. Also make sure it is not on mute since it seems to default to a mute state and also change the level for output to 100%. 

I would still like to know what caused the issue in the first place but for now it is fixed. I now go back to watching movies without closed captioning.

---

