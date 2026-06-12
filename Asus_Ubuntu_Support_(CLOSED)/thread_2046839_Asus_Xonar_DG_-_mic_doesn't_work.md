---
title: "Asus Xonar DG - mic doesn't work"
date: 2012-08-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by trove on 2012-08-23
I've got a problem with my Xonar device. Output works allright, but my mic doesn't. Every spectrogram stays calm, only my USB camera's mic works (but it's pitiful). I've already checked every capture combinations in alsamixer with no success. 

```
01:08.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
   Subsystem: ASUSTeK Computer Inc. CMI8786 (Xonar DG)
   Kernel driver in use: snd_oxygen
```

```
snd_oxygen             20962  3 
snd_oxygen_lib         41445  1 snd_oxygen
snd_usb_audio         122982  1 
snd_pcm                97188  3 snd_oxygen_lib,snd_usb_audio
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_page_alloc         18529  1 snd_pcm
snd_mpu401_uart        14169  1 snd_oxygen_lib
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            30748  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_seq,snd_rawmidi
snd                    78855  18 snd_oxygen,snd_oxygen_lib,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_mpu401_uart,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
soundcore              15091  1 snd
```

PS idk if this is a proper category, but still it's some Asus, isn't it?

---

