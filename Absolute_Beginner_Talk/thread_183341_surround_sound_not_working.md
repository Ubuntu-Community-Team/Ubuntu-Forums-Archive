---
title: "surround sound not working"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by nick5449 on 2006-05-27
I have a 4.1 speaker system and a sound blaster live sound card.  My back two speakers arent working...is there a driver that I need? Or somewhere in the settings where I can change it to 4.1?  When I go to System > Preferences > Sound, it recognized my sound card (SBLive 5.1).  Thanks

---

### Post by Sutekh on 2006-05-27
I might be able to help if your SB card is the same as mine.

This command will list the type of sound card
```
lspci | grep audio
``` This command will list the sound drivers you have installed
```
lsmod | grep snd
```

---

### Post by Mission 10 on 2006-05-27
I had the same problem but it was a matter of enabling those other speakers.

Applications--Sound and Video--Volume Control--Edit--Then select which speakers you wish to enable and set the sound level.

Hope that helps.

---

### Post by nick5449 on 2006-05-28
```
nick@Nick:~$ lspci | grep audio
0000:00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
nick@Nick:~$ lsmod | grep snd
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117156  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         92704  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
snd                    55268  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10208  1 snd

```

> I had the same problem but it was a matter of enabling those other speakers.

Applications--Sound and Video--Volume Control--Edit--Then select which speakers you wish to enable and set the sound level.

Hope that helps.

When I go there and enable 'surround' it appears under the capture tab, not the playback tab.  I dont see any other options that would let me enable the back speakers.  Also, what does PCM stand for under those settings?

Thanks!

---

### Post by joshrobinson on 2006-05-28
pcm is just an audio type.. if you change the slider on that it effects any sounds you have such as mp3's wav files, login sounds and system sounds

---

### Post by Sutekh on 2006-05-28
Have you opened 
```
alsamixer
```
to make sure all channels are up?  This might be the same as the Volume Control though.

If they are turned up, have you tried setting the sound output from an application to 5.1 instead of stereo?  XMMS/BMP or Totem have these options in their preferences.

The last thing to try is to create an .asoundrc file.  This is one particular method.  I use a different one too.

[http://ubuntuforums.org/showthread.php?t=167986](http://ubuntuforums.org/showthread.php?t=167986)

---

