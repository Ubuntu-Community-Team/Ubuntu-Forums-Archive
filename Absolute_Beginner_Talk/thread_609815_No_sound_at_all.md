---
title: "No sound at all"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by atlascomplete on 2007-11-11
I am getting no sound at all coming out of my laptop when I boot into Ubuntu 7.10. I am using a 82801H (ICH8 Family) HD Audio Controller by Intel. I know the sound card work because when I boot into Vista, it works fine.

Is there a driver that not installed or something?

---

### Post by matthewcraig on 2007-11-11
It is most likely muted in your ALSA settings.

---

### Post by atlascomplete on 2007-11-14
> **matthewcraig said:**
> It is most likely muted in your ALSA settings.

Where can I find this? The only place I can find anything remoted related to ALSA settings is the track mixer from where I can choose Alsa mixer or OSS mixer in the Sounds window.

---

### Post by Surkow on 2007-11-14
> **atlascomplete said:**
> Where can I find this? The only place I can find anything remoted related to ALSA settings is the track mixer from where I can choose Alsa mixer or OSS mixer in the Sounds window.

Run the command "alsamixer" in the terminal. I will give you a simple text based gui where you change the master volume etc.

---

### Post by Ub1476 on 2007-11-14
Or maybe:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

