---
title: "[SOLVED] how to tell if Soundblaster is enabled?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Abacab on 2008-02-17
Hi.

I'm new to Ubuntu and Linux and last week managed to successfully dual boot our new Vista PC with Gutsy, thanks to some great advice given here by some helpful posters. 

So far everything has gone well and I'm actually amazed how easy I've found the transition. However, I have one question that may be a stupid one but I don't know how to find the answer.

My PC came with onboard sound but I had them add a Soundblaster Audigy SE card when it was being built. I am getting sound okay but not as good as it was on Vista. I'm wanting to know how I find out if Gutsy is using my Soundblaster card or the onboard? I've looked everywhere but can't find any settings. If only I could find it then if needs be the onboard can be disabled. Any advice greatly appreciated.

---

### Post by herbster on 2008-02-17
AFAIK, you should disable the onboard sound in your system BIOS when you install an add-on sound card. To find out your sound situation try:

```
lsmod | grep snd
```

and

```
lspci | grep Audio
```

This should tell you if it actually reads the SB card, for starters. If it shows the SB in this output, then open up the gnome-volume-control, try File > Change Device  and see if you see the 2 devices there. If you see "CA0106" or something similar, that's the SB card. Select that, then edit the volume levels as desired.

---

### Post by mattismyname on 2008-02-17
Which do you have the speakers plugged into?  If you have them plugged into the SB, then it's using that.  If they're plugged into the builtin jack, then they're using the onboard sound device.

---

### Post by Abacab on 2008-02-19
Herbster, lsmod | grep snd gives the following:

snd_rtctimer            4384  0 
snd_usb_audio          81024  0 
snd_usb_lib            17920  1 snd_usb_audio
snd_hwdep              10244  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_ca0106             34720  1 
snd_ac97_codec        100644  1 snd_ca0106
snd_seq_midi            9600  0 
snd_pcm_oss            44672  0 
snd_rawmidi            25728  3 snd_usb_lib,snd_ca0106,snd_seq_midi
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_pcm                80388  4 snd_usb_audio,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  14 snd_usb_audio,snd_hwdep,snd_seq_oss,snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_rawmidi,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm
usbcore               138632  8 snd_usb_audio,snd_usb_lib,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd


CA0106 is listed in the volume control. Regarding the bios, I remember that I did manually disable the onboard sound through device manager on Vista so they may not have disabled it before shipping.

mattismyname, I can't believe that never occurred to me. I feel rather foolish now. They are connected to the SB card. Thanks.

---

### Post by herbster on 2008-02-19
So it's working?? Change your original thread title to [SOLVED] before the title if so, for others in the future searching.

---

### Post by Abacab on 2008-02-19
I presume so. Thanks for your help.

---

