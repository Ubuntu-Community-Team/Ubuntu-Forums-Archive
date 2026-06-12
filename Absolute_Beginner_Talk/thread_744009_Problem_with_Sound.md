---
title: "Problem with Sound"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by n.arjunb on 2008-04-03
I have Ubuntu Gutsy Gibbon in my comp along with Windows Vista Premium.
The Sound in Ubuntu will be working and incase i restart and log to windows and back again to ubuntu, there will be no sound, even though the sound card is recognized.........
AND it is not muted.   Can anyone please help me?

---

### Post by n.arjunb on 2008-04-03
Hello!!!
Can anyone please help me....I am getting pained :(

---

### Post by taavikko on 2008-04-03
No need to bump your message up in 10 minutes.

After you've logged on to windows, and back again, what does command say?
```
lsmod |grep snd
```

---

### Post by n.arjunb on 2008-04-03
snd_hda_intel         263712  5
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


This is what it says......Can you please tell me what is wrong with it?

---

