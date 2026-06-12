---
title: "Battery and sound problem"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by mirco_paronetto on 2007-10-23
Hi, I have a first generation macbook. I use linux for work and I decided to install the ubuntu distro.
I have the gutsy gibbon version.
Unfortunately I have two problems:
1: the battery life is very short, I use powertop to kill the useless processes and still I reach a 1.50, 1.55h life, that's very bad.
In the powertop list the process that use more power is an interrupt and I dont get what is for.
2: I can't completely turn off the sound...if not with alsamixer....If I turn it off with F3 key or I lowerer the volume it still work, it seems like the sound change...but not turn off.
Has someone else got these problems? Can someone please help me?

---

### Post by volanin on 2007-10-25
> **mirco_paronetto said:**
> Hi, I have a first generation macbook. I use linux for work and I decided to install the ubuntu distro.
I have the gutsy gibbon version.
Unfortunately I have two problems:
1: the battery life is very short, I use powertop to kill the useless processes and still I reach a 1.50, 1.55h life, that's very bad.
In the powertop list the process that use more power is an interrupt and I dont get what is for.
2: I can't completely turn off the sound...if not with alsamixer....If I turn it off with F3 key or I lowerer the volume it still work, it seems like the sound change...but not turn off.
Has someone else got these problems? Can someone please help me?

1. I have posted a thread with some tips for lowering battery usage.
Check it out here: [Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=590867").
There are even more tips out there if you search, that could help you.

2. The sound comes from two places in alsa: The PCM channel and the FRONT channel.
When you press F3, only the PCM channel is muted. So the sound is not completely silenced.
To fix this, go into SYSTEM -> PREFERENCES -> SOUND and down there, in the Default Mixer Tracks,
select BOTH the PCM and FRONT channels using CTRL + click.

Also, if you prefer, enable maximum SURROUND in alsamixer.
The sound will be a LOT better!

---

### Post by cyberdork33 on 2007-10-25
> **volanin said:**
> 2. The sound comes from two places in alsa: The PCM channel and the FRONT channel.
When you press F3, only the PCM channel is muted. So the sound is not completely silenced.
To fix this, go into SYSTEM -> PREFERENCES -> SOUND and down there, in the Default Mixer Tracks, select BOTH the PCM and FRONT channels using CTRL + click.
Nice tip, I didn't realize you could multi-select there!

---

