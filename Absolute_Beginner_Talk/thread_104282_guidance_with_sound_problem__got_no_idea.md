---
title: "guidance with sound problem?  got no idea"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Fibre on 2005-12-15
I've just installed ubuntu a couple of days ago and it's running ok I think lol.

One ongoing problem that I havn't seen any answers to yet is sound. Every time I boot up with Ubuntu it can't make it's mind up. It's worked maybe 2 times out of about 5 boot ups.

If you can give me some guidance - where to look or what to do?

Thanks for all help in advance.

Also the software for the intergrated sound I have has a program should I use it ?
Can I use it ? I'm assuming the answer is no or maybe? :???: :) 

Any how here is what I have :-

PX8 Neo-V m/b with intergrated sound

*AC97 link controller intergrated  in VT8237
*VIA VT1617 6-channel audio codec
   - Compliance with AC97 v2.2 Spec
   - Meets PC2001 audio performance requirement   

This comes from my manual and the manual relates to   3  variations of this board so I'm not 100% sure in regards to VT8237 / VT1617  part of the discription although I'm assuming it relates to all 3 boards with both used in all.

The program that came with the intergrated sound is called -  vinyl

:( :smile:

---

### Post by Fibre on 2005-12-15
Here's what I've worked out so far with my system if it helps out all

snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  2
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  14 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd

I don't really know what I'm talking about here but it looks to me as if it has the wrong codec installed ? hmm

---

