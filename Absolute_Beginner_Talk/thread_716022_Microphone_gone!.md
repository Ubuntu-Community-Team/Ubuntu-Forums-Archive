---
title: "Microphone gone!"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2008-03-05
This seems an old issue, but I'd like to make it current, as my microphone worked yesterday, and today it doesn't! I have a headset plugged in (not usb), which also has been working for months.

Here are some pertinent outputs:

From debug for gnome sound recorder:

```
jared@jared-laptop:~$ gnome-sound-recorder --gst-debug-level=2
0:00:00.246958000  7718 0x805e408 WARN                  alsa pcm_hw.c:1242:snd_pcm_hw_open: alsalib error: open /dev/snd/pcmC0D1c failed: Device or resource busy
0:00:00.247102000  7718 0x805e408 WARN                  alsa gstalsasrc.c:596:gst_alsasrc_open:<alsasrc0> error: Device 'plughw:0,1' is busy
```

and aplay -l

```
jared@jared-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any suggestions, tips, tricks, empathy is welcome!

--Jared

---

### Post by jaredssix on 2008-03-06
FYI:
I did a system restore to two weeks back in windows (dual boot system), thinking that if I went back to when the mic worked, it might work--it doesn't work.

I tried two other mics, which do work on my system.

The mic I have been using on my system (and which is no longer working on my system) works on other computers.

---

