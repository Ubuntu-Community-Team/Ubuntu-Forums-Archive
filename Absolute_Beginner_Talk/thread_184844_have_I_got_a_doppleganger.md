---
title: "have I got a doppleganger?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-05-30
Another tale of lament and woe with soundcards and Dapper!
Sound used to work on Ubuntu breezy, now I've upgraded to Xubuntu Dapper, and have no sound. 
Or so I believe, Xfmedia behaveas as though its playing an mp3 correctly, I've installed codecs, and so on.

Output from lspci | grep audio:

0000:00:0d.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

IS THIS THE PROBLEM? Surely I shouldn't have two in here?  But I know nothing, so I thought I should check with you knowledgable types first ;-)

Output from lsmod | grep snd:

snd_cmipci             34336  2
gameport               15496  1 snd_cmipci
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_opl3_lib           10624  1 snd_cmipci
snd_timer              25220  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd_mpu401_uart         7808  1 snd_cmipci
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd                    55268  14 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd

Is there any kind of diagnostic howto for these soundcard problems, like the one for wireless cards?  there seem to be alot of peeps with similar problems and unsure what to do.....


Cheers everyone

BTW just thought I'd say to you all what a great and helpful forum this is, easily the best I've come across in all the net, you're all tops:KS 

Sorry to eulogise so much, but its been nice and sunny here today.....:-)

---

### Post by Lord Illidan on 2006-05-30
I think a fresh install of Dapper might fix the problem..

---

### Post by damianubuntu on 2006-05-30
I just did apt-get update and apt-get dist-upgrade.
That didnt fix it, is a fresh install more throrough then?

---

### Post by Lord Illidan on 2006-05-30
[quote=damianubuntu]I just did apt-get update and apt-get dist-upgrade.
That didnt fix it, is a fresh install more throrough then?[/quote]

Yes. You upgraded from breezy right? A fresh install would wipe out all ancient config files... thus being very much more thorough. Just backup your /home first.

---

### Post by damianubuntu on 2006-05-30
Actually I did a clean install with a downloaded Dapper iso, this was some weeks ago.  Then eventually today thiking I must get to grips with the sound, did the dist-upgrade, but I guess what you're saying would still apply.
I'll let you know how it gets on.  Thanks m'lord ;-)

---

### Post by Lord Illidan on 2006-05-30
[quote=damianubuntu]Actually I did a clean install with a downloaded Dapper iso, this was some weeks ago.  Then eventually today thiking I must get to grips with the sound, did the dist-upgrade, but I guess what you're saying would still apply.
I'll let you know how it gets on.  Thanks m'lord ;-)[/quote] 
Hold on a moment. You had no sound even after the clean install? Because then the problem is a Dapper problem, rather than an upgrade problem.

EDIT : Try this solution : [http://www.ubuntuforums.org/showpost.php?p=776658&postcount=2](http://www.ubuntuforums.org/showpost.php?p=776658&postcount=2)

---

### Post by richbarna on 2006-05-30
I had a sound problem with a Dapper upgrade, I was using the KDE desktop and I  downloaded the ubuntu-desktop. Then I installed the latest Dapper Automatix and everything is suddenly working.
And I mean EVERYTHING, even amarok.

---

### Post by damianubuntu on 2006-05-31
Lord Illidian:
OK, so I disconnected and reinstalled before reading your final comment!  Anyway at least I know it is now clean of any messing about of mine.  I did a Dapper server install and then apt-get install xubuntu desktop.

Richbarna:
I also did Automatix 6.1 for dapper, though m guess is that Automatix would solve codec problems rather than anything else (?)  

Anyway Beep and Xfmedia both show tracks being played OK, but I still have not a whisper from the sound, although I did notice a slight hiss when starting to play a track, suggesting that at least some kind of connecction is being made, and I can rule out unplugged cables, burnt out card and so on.

More importantly I still have the doppleganger effect with lspci, though since its an onboard unit rather than a simple card, i wonder whether I'm reading too much into this.

So has anyone got any further suggestions?

Thanks all

EDIT: following on from some more searching, heres the output from more /dev/sndstat just in case:

Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux bed 2.6.15-20-386 #1 PREEMPT Tue Apr 4 17:48:51 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0xdc00, irq 11
C-Media PCI CMI8738-MC6 (model 39) at 0xda00, irq 9

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)
1: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: CMedia PCI
1: CMedia PCI

---

