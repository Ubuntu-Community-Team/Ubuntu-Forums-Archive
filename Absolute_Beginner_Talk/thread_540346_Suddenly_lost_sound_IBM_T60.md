---
title: "Suddenly lost sound IBM T60"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by cognitive on 2007-09-01
I've just booted my Ubunutu 7.04 and wanted to watch a movie but there is no sound. I checked with alsamixer but it said:

alsamixer: function snd_ctl_open failed for default: No such device

...well this is already beyond my knowledge :(


Maybe someone can help me out :)

---

### Post by cognitive on 2007-09-01
Did the following things

cat /proc/asound/cards
--- no soundcards ---


sudo lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at ee400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

lsmod | grep snd
snd_pcm_oss            44672  0 
snd_pcm                81028  1 snd_pcm_oss
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35200  0 
snd_seq_midi            9728  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54128  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56452  9 snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  1 snd_pcm

---

### Post by wolfen69 on 2007-09-01
try this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards)

---

### Post by cognitive on 2007-09-01
> **wolfen69 said:**
> try this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards)


Adding the line did not help but re-installing Alsa solved the issue. thanks a lot

---

