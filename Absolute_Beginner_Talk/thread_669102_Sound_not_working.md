---
title: "Sound not working"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by ankit07 on 2008-01-16
Hey..
I just now installed ubuntu 7.10 on my computer... Everything is working fine except that the sound is not working.. It is detecting the alsa sound driver but still no sound is coming...
Wat should i do???

---

### Post by Ted D. on 2008-01-16
I have the same problem since I loaded Gutsy a few months ago. Despite following recommendations posted - which I have followed - I have not been able to crack the problem. The odd thing is that I have gone through Breezy, Dapper, & Feisty and have never had that problem before. One would think that this change could be easily remedied.
sadly not.

---

### Post by tigerplug on 2008-01-16
> **ankit07 said:**
> Hey..
I just now installed ubuntu 7.10 on my computer... Everything is working fine except that the sound is not working.. It is detecting the alsa sound driver but still no sound is coming...
Wat should i do???

Make and Model Please?

---

### Post by c0met on 2008-01-16
Have you double checked that the particular aspect of sound that you are trying to reproduce is not muted? You can check this by double-clicking on the speaker icon near the log-out icon. When you open the sound mixer, you should also have a look under Edit >> Preferences to double check that the mixer has the appropriate controls displayed.

---

### Post by pndragon on 2008-01-16
I had the same problem when I first installed gutsy. The first updates shutdown my sound. It was really frustrating until I got it worked out.

Try
```
alsamixer
```
from a terminal window. This will show you a graphical representation of the alsamixer attached to your sound card. Use your <> arrow keys to go through the columns. If it says "MM" in the small box at bottom, you need to unmute it with the M key. Increase the volume with the up arrow key.

Restart.

This took care of it for me.

---

### Post by ankit07 on 2008-01-16
> **tigerplug said:**
> Make and Model Please?

i am using ubuntu gusty gibbon 7.10... My motherboard is intel 945G... I also installed debian and had the same problem....

---

### Post by Dave Otter on 2008-01-16
Applications-Accessories-Terminal
                     type in     asoundconf list

                                            this will give soundcards 

    if 2 or more open terminal

                 type in       asoundconf set-default-cardCARD

                           replacing CARD with the card that works best for you.
    

             If you have more than 1 card and the above does not work try to disable inbuilt sound in BIOS

---

### Post by ziky on 2008-01-16
Hello 
My problem *seems* related to ankit07's one.

Three days after a Gutsy reinstallation, and many normal boots, the sound suddenly disapeared. I never had sound problem with alsa on Ubuntu, and the sound works on Windows. 
I found no relevant errors on logs. The physical sound switch is on, and alsamixer doesn't shows any mute level either. ESD mixing is disabled. I've reinstalled alsa but it didn't help.

Here are useful outputs :
```

asoundconf list
Names of available sound cards: ICH6

lspci | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

cat /proc/asound/modules
 0 snd_intel8x0

```
```

lsmod | grep snd
snd_intel8x0           34076  1 
snd_ac97_codec        100132  1 snd_intel8x0
ac97_bus                2432  1 snd_ac97_codec
snd_pcm_oss            43392  0 
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                77960  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4100  0 
snd_seq_oss            33920  0 
snd_seq_midi            8832  0 
snd_rawmidi            25088  1 snd_seq_midi
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                51440  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23044  2 snd_pcm,snd_seq
snd_seq_device          8844  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc         10376  2 snd_intel8x0,snd_pcm

```
```

lsof /dev/snd/*
COMMAND     NAME
mixer_app   /dev/snd/controlC0

```
aplay -l and  modprobe snd-intel8x0 are both succesfull.

I tried to solve this by myself before coming here but I'm a beginner and that doesn't help. Thanks a lot for your attention.

---

### Post by ankit07 on 2008-01-17
> **pndragon said:**
> I had the same problem when I first installed gutsy. The first updates shutdown my sound. It was really frustrating until I got it worked out.

Try
```
alsamixer
```
from a terminal window. This will show you a graphical representation of the alsamixer attached to your sound card. Use your <> arrow keys to go through the columns. If it says "MM" in the small box at bottom, you need to unmute it with the M key. Increase the volume with the up arrow key.

Restart.

This took care of it for me.

I did wat u told bu still the sound is not coming.. I unmuted all in the alsamixer and then restarted.... Still not coming...

---

### Post by ankit07 on 2008-01-17
> **c0met said:**
> Have you double checked that the particular aspect of sound that you are trying to reproduce is not muted? You can check this by double-clicking on the speaker icon near the log-out icon. When you open the sound mixer, you should also have a look under Edit >> Preferences to double check that the mixer has the appropriate controls displayed.

I have double clicked on the that cand the sound is not muted... There is no sound not even while i am logging in or logging out..

---

### Post by quanumphaze on 2008-01-17
In the terminal type:
```
lspci -v
```
This will display a very long list of some of your hardware. Somewhere there is the model of your sound card.

---

### Post by ziky on 2008-01-17
Hello 
Problem solved for me !
Using alsamixer, by muting Headphone Jack Sense and Line Jack Sense, the sound came back, don't ask me why...

---

### Post by ankit07 on 2008-01-18
> **quanumphaze said:**
> In the terminal type:
```
lspci -v
```
This will display a very long list of some of your hardware. Somewhere there is the model of your sound card.

output of #lspci -v 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Intel Corporation Unknown device 0204
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 501c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

---

### Post by quanumphaze on 2008-01-19
> **ankit07 said:**
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Seems like you have the same one I have.

I had to recompile ALSA from source.

These few links may help you out:
[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")
[HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
[Gutsy Intel HD Audio Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

Remember to get the latest ALSA sources.

The real problem comes when guessing what model you should use in /etc/modprobe.d/alsa-base

---

### Post by Casual Fan on 2008-01-19
The comprehensive guide referenced above is teh bomb. Highly recommended.

---

### Post by ankit07 on 2008-02-21
First of all i want to thank quanumphaze for giving me the links...

My problem was still not solved by doing the things giving in that.. Finally after 2 months of trying i got my sound back.. "good so far?"

now listen to this>>>

i already had added the modprobe file to have option=3stack(may be this did the trick)...
AND
 for some reason after few weeks  i changed the output port from the green port to the blue port(even pink)..
AND
 intriguingly it started working... (am i to be thrilled!!!)

however, now when i use VLC player after sometime the sound goes off (though the system sound test is working fine). i think that vlc somehow corrupted the codecs..

---

