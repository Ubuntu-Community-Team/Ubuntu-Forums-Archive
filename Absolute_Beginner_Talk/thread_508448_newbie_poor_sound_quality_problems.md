---
title: "newbie poor sound quality problems"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-24
I just installed Feisty and the sound quality is poorer than what I had in Windows XP. 
One problem is that somehow, there's always a sound on my headphones like background static - whether I'm playing something or not.
Also, when I listen to music (using any music player), the sound cracks on high notes (in addition to the horrible background buzz).
Why is this happening and how do I fix it?
Thanks.

---

### Post by opossumjack on 2007-07-24
Hi...
Are the headphones ok? Have you tried them on another computer/hardware?

What kind of sound server are you using?

---

### Post by MrHippocampus on 2007-07-24
Ive seen this problem on a friends laptop, I have no idea whether you using a similar sound card or not so these instructions may not work, but ill post them anyway.

Open up a terminal and type in "alsamixer", this will give you a list of loads of volume bars for different parts of your sound card, try playing music and seeing what effect any of these have on it (on my freinds laptop I found that moving one slider to around 25% stopped the crackling and another slider could be used to change the volume after that). Navigate with left and right keys, move the sliders with the up and down keys.

If you press tab you will move to a different set of bars, these are to do with recording, set all of these to 0 as they might be picking up sound and interfering with the music.

---

### Post by kleo skywalker on 2007-07-25
> **opossumjack said:**
> Hi...
Are the headphones ok? Have you tried them on another computer/hardware?

What kind of sound server are you using?

The headphones are ok, and they were working fine with Windows XP.
I had to look up Wikipedia to find out what sound server means, and then I checked system processes, and I think it's **esd**.
What next?

---

### Post by kleo skywalker on 2007-07-25
> **MrHippocampus said:**
> Ive seen this problem on a friends laptop, I have no idea whether you using a similar sound card or not so these instructions may not work, but ill post them anyway.

Open up a terminal and type in "alsamixer", this will give you a list of loads of volume bars for different parts of your sound card, try playing music and seeing what effect any of these have on it (on my freinds laptop I found that moving one slider to around 25% stopped the crackling and another slider could be used to change the volume after that). Navigate with left and right keys, move the sliders with the up and down keys.

If you press tab you will move to a different set of bars, these are to do with recording, set all of these to 0 as they might be picking up sound and interfering with the music.

Thanks.
I installed ALSA Mixer from Add/Remove - it's the graphical interface to do what you suggested. I've been able to silence the background buzz on my headphones using one of the bars. However, I haven't been able to satisfactorily deal with the sound cracking at high pitches yet - when I reduce the playback volume (I think that's the master volume - it's the one I can control using the volume buttons on my keyboard) a bit, sounds better but then the volume's not high enough (it's the maximum on my music player). Permanent solution to this will be welcome.

---

### Post by kleo skywalker on 2007-08-07
Still having this problem - sound cracks horribly at even slightly high pitches. Can't enjoy music at all.
Please help.

---

### Post by kleo skywalker on 2007-08-10
I recently switched from Windows XP to Ubuntu Feisty. The sound quality on Feisty is very poor. Sound breaks and cracks on even slightly high pitches and listening to music is far from enjoyable.
I know that my hardware is ok because I was getting excellent sound quality in XP with the exact same hardware.
I've also tried different music players, and fiddled with some of the settings in ALSA Mixer (using the GUI) but all in vain.
Can someone please help me figure out why this might be happening and what I can do to fix it? I really don't want to give up Feisty for something like this.
Thanks.
P.S.: I posted about this  [here]("http://ubuntuforums.org/showthread.php?t=508448"), but my problem remains.

---

### Post by Dr Small on 2007-08-10
Have you tried using different sound players, such as totem, vlc, mplayer, audacity and such?

Dr Small

---

### Post by kleo skywalker on 2007-08-10
> **Dr Small said:**
> Have you tried using different sound players, such as totem, vlc, mplayer, audacity and such?

Dr Small

Yes I have, as I clearly mentioned in my post.

---

### Post by asmoore82 on 2007-08-10
Open "System -> Preferences -> Sounds"
and Turn Off software mixing!!

then 'killall esd'

---

### Post by kleo skywalker on 2007-08-10
> **asmoore82 said:**
> Open "System -> Preferences -> Sounds"
and Turn Off software mixing!!

then 'killall esd'

In basic terms, what does this mean and what will it do?

---

### Post by kleo skywalker on 2007-08-11
> **asmoore82 said:**
> Open "System -> Preferences -> Sounds"
and Turn Off software mixing!!

then 'killall esd'

What is software mixing, and what does killall esd do? Also, if this doesn't help, how do I reverse the killall esd?

---

### Post by kleo skywalker on 2007-08-13
> **asmoore82 said:**
> Open "System -> Preferences -> Sounds"
and Turn Off software mixing!!

then 'killall esd'

Tried it. Doesn't improve the sound - at least not perceptibly.

Please help!

---

### Post by bapoumba on 2007-08-13
Thread merged in the pre-existing one.

---

### Post by kleo skywalker on 2007-08-13
> **bapoumba said:**
> Thread merged in the pre-existing one.

Umm... I had to post a new thread because of lack of responses here. Was that a major problem?

---

### Post by bapoumba on 2007-08-13
> **kleo skywalker said:**
> Umm... I had to post a new thread because of lack of responses here. Was that a major problem?
Nope, but two open threads on the same subject can be difficult to follow. In addition, if you get one of them solved, this means the other one remains unsolved, and cannot help  anyone with the same problem.
The forums are huge, so better keep one issue in one thread.

You can bump a thread, say once or twice per 24 hours, while the issue is not solved. Once it is, you can go to the "thread tools" menu, and mark it solved ;)

---

### Post by kleo skywalker on 2007-08-14
Bump

---

### Post by kleo skywalker on 2007-08-15
**[size="7"]bump[/size]**

---

### Post by ADT on 2007-08-15
I had the same problem.

What fixed it for me was to change the sound settings using the terminal program alsamixer.

Open a terminal emulator by going  to applications menu and find it in there.

Type alsamixer inside the terminal.

A display will pop up like this
    [    ]                [      ]                 [    ]
    [    ]                [      ]                 [    ]
    [    ]                [      ]                 [    ]
    [00]                [MM]                [00]
Master           Master M            PCM

Use the left and right arrow buttons to move between the Items in alsamixer. Use the m key to turn an Item on. It is on if 00 is displayed at the bottom.

Move to PCM and change its volume setting to a level where its [dB gain=0.00, 0.00]. For me the level was 74.

This worked for me I dont know if it will work for you.

---

### Post by ashwinhgtx on 2007-08-15
Even I've got the same problems on my Thinkpad R60. But it's only when playing movies. Music is fine.

---

### Post by sabthagiri on 2007-08-15
Hi All, I am also facing the same problem. Did anyone solve it? Here is a gist of the problems that I am facing:

1. When a audio is playing and I change the volume at the volume bar (by clicking the volume icon on the top right) I am no longer able to hear any audio. I had to reboot ubuntu to get audio again. :confused:

2. I originally got a static sound in the background when I play music. Then I tried running alsa mixer and changing the setting for the PCM bar. It helped fixing the static in the background, but  I still get a "coarse" sound at high frequencies. :(

I am using Asus M2NMX board with on board Sound MAX (Analog devices). The sound is working perfectly fine in Win XP.

TIA.

---

### Post by kleo skywalker on 2007-08-15
> **ADT said:**
> I had the same problem.

What fixed it for me was to change the sound settings using the terminal program alsamixer.

Open a terminal emulator by going  to applications menu and find it in there.

Type alsamixer inside the terminal.

A display will pop up like this
    [    ]                [      ]                 [    ]
    [    ]                [      ]                 [    ]
    [    ]                [      ]                 [    ]
    [00]                [MM]                [00]
Master           Master M            PCM

Use the left and right arrow buttons to move between the Items in alsamixer. Use the m key to turn an Item on. It is on if 00 is displayed at the bottom.

Move to PCM and change its volume setting to a level where its [dB gain=0.00, 0.00]. For me the level was 74.

This worked for me I dont know if it will work for you.

I've already tried all this using the graphical interface for ALSA Mixer (as I posted on page 1 of this thread)  - sound still cracks on high pitches.

---

### Post by ADT on 2007-08-15
Sorry, I just read your post on the first page. 

I dont know what else there is that can fix sound problems.

Theres a different sound driver called OSS, maybe using that would solve the problem but I wouldn't be able to guide you through the setup as I've never used it. Its an older sound driver that was used on 2.4 kernels.

---

### Post by sabthagiri on 2007-08-15
Hi All,
Found the following article on the official Ubuntu Help Community site:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The symptoms listed here look similar to what we guys are facing. I tried it out and it worked for me. :guitar:  Think we need to recompile ALSA drivers.

Cheers!

---

### Post by kleo skywalker on 2007-08-18
> **sabthagiri said:**
> Hi All,
Found the following article on the official Ubuntu Help Community site:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The symptoms listed here look similar to what we guys are facing. I tried it out and it worked for me. :guitar:  Think we need to recompile ALSA drivers.

Cheers!

Thanks. I've never compiled from source before, so a bit apprehensive. Also, this is for Ubuntu 6.06, will it work ok for Feisty? And how do I know Feisty doesn't already use this version of ALSA?

---

### Post by medicineman24 on 2007-10-19
Make sure PCM/Headphone volume isn't at 100% but rather about 80%

---

