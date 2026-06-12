---
title: "Sound in Kubuntu after upgradee"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by CrystalWitch on 2007-10-02
I am brand new to Kubuntu (and Linux). I have an ACER Aspire 5051 and when I was testing with the live CD of 7.04 at first I couldn't get sound, but after a bit of playing with Kmix, everything seemed to be OK, so I did the install,and everything seemed OK. A couple of days ago there were a whole load of updates, so I upgraded the system. Since then I've had a problem with sound. I can't hear anything from the speakers. If I plug speakers into the headphone jack, I get no sound on the left channel, and it is very quiet on the right channel. If I use headphones, there is a little sound on the left, and more on the right. Kmix has changed - things like the surround slider are gone. If it makes a difference, I'm using the AMD64 version of Kubuntu

I don't know enough yet to do much. Can anyone help? I've read a lot of things on forums, most are for ubuntu not kubuntu, but I've seen requests for output from a couple of commands, so...


suzie@Phoenix:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


suzie@Phoenix:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xb0000000 irq 16


suzie@Phoenix:~$ lsmod | grep snd
snd_hda_intel          24224  6
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49408  0
snd_mixer_oss          19840  2 snd_pcm_oss
snd_pcm                92808  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0
snd_seq_oss            36608  0
snd_seq_midi           11008  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  4 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  2 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm

If you can help, it really needs to be at absolute novice level...

Thank you

---

