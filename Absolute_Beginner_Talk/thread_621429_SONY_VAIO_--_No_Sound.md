---
title: "SONY VAIO -- No Sound"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by nightgh0st on 2007-11-23
Yes, *again* a "no sound" post.. this time from a Sony Vaio.. In the screen-shot you can see the type of the sound card.. Honestly guys, I used all my knowledge about computers (which is not much, if any) and could not get it to work.. everything else seems to be working perfectly fine.. any suggestions?

---

### Post by jmc1024 on 2007-11-23
If you do lsmod | grep -i snd do you get anything like below?
snd_hda_intel          21912  3 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

---

### Post by mysticgal27 on 2007-11-23
Hi,
I am having a problem with my sound and wireless system. It was working fine before but as i was trying to fix the cube setting..everything got messed up and now i cant make it work. Can anyone help me? My laptop is Sony Vaio VGN-FZ140E

---

### Post by nightgh0st on 2007-11-24
> **jmc1024 said:**
> If you do lsmod | grep -i snd do you get anything like below?
snd_hda_intel          21912  3 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

Here is what I get when I write that command, its attached.. what does that tell me?

---

### Post by nightgh0st on 2007-11-24
/bump ^_^

---

