---
title: "Apple thunderbolt does not wake up after hibernation"
date: 2016-12-30
forum: Apple Hardware Users
---

### Post by biocyberman on 2016-12-30
I use a dual monitor, one iMac and one thunderbolt display. Whenever I wake the computer up from suspension or hibernation, the thunderbolt computer is totally black. I can however use shortcut keys to move an application (i.e. Firefox) from the thunderbolt screen to the iMac screen. So the app running there do not die together with the screen. How do I bring back the thunderbolt screen without restart the computer ? (Running Ubuntu 16.04)

Some information below

```

~ &#10148; diff modbeforehibernate.txt modafterhibernation.txt                                                                                                                                                                             
43c43
< snd_usb_audio         176128  2
---
> snd_usb_audio         176128  0
73c73
< snd                    81920  27 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
---
> snd                    81920  23 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
~ &#10148; locate thunderbolt                                                                                                                                                                                                    
/lib/modules/4.4.0-28-generic/kernel/drivers/thunderbolt
/lib/modules/4.4.0-28-generic/kernel/drivers/thunderbolt/thunderbolt.ko
/usr/share/plainbox-provider-checkbox/jobs/thunderbolt.pxu
/usr/src/linux-headers-4.4.0-28/drivers/thunderbolt
/usr/src/linux-headers-4.4.0-28/drivers/thunderbolt/Kconfig
/usr/src/linux-headers-4.4.0-28/drivers/thunderbolt/Makefile
/usr/src/linux-headers-4.4.0-28-generic/include/config/thunderbolt.h
~ &#10148; sudo modprobe thunderbolt                                                                                                                                                                                             
~ &#10148; lsmod |grep thunderbolt                                                                                                                                                                                               
thunderbolt            53248  0

```

---

### Post by howefield on 2016-12-31
Thread moved to the "*Apple Hardware Users*" forum.

---

