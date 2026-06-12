---
title: "Mac mini (Intel) and no sound with 12.04LTS"
date: 2014-04-09
forum: Apple Hardware Users
---

### Post by sakari.aaltonen on 2014-04-09
I had 11.04 working well on an Intel-based Mac mini for years, but then support stopped and I switched to 12.04LTS. Things continue to work well, except for sound which does not work at all. Here is the output from *lsmod |grep snd*:
```
snd_hda_codec_hdmi     31823  3 
snd_hda_codec_cirrus    23322  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
```

That looks like a lot of modules. But all they produce is silence.

Can anybody help?

---

### Post by frank18 on 2014-04-14
> **sakari.aaltonen said:**
> I had 11.04 working well on an Intel-based Mac mini for years, but then support stopped and I switched to 12.04LTS. Things continue to work well, except for sound which does not work at all. Here is the output from *lsmod |grep snd*:
```
snd_hda_codec_hdmi     31823  3 
snd_hda_codec_cirrus    23322  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
```

That looks like a lot of modules. But all they produce is silence.

Can anybody help?

This should help you out i know it did to me.

[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

---

### Post by sakari.aaltonen on 2014-04-14
> **frank18 said:**
> This should help you out i know it did to me.

[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

Thank you, but this is an Intel-based Mac mini. That is, it is not a PowerPC machine.

---

