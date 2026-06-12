---
title: "No sound through Headphone Jack"
date: 2009-05-31
forum: Apple Hardware Users
---

### Post by Clement_User on 2009-05-31
Hello all, this is my first post. I am currently using Kubuntu 9.04 through Wubi on an iMac 24". I love Kubuntu, though I cannot stand the lack of output through the headphone jack. They work in XP and OS X. I'm really confused. The internal speakers work just fine, but there simply is no output through the external speakers that I have plugged in. 

I have OS X and XP as a dual-boot, of which the XP partition leads to a Wubi install. I didn't do a triple boot because on a Mac, the instructions feel inherently "hack"-ish.

I'm pretty sure I have a ALC 885 sound card. What other information should I post? I've been trying many solutions, though I haven't tried other ALSA drivers. Editing alsa-base.conf doesn't help (tried model=imac24 and model=mbp3). I have tried reinstalling many times. Going to the terminal and typing alsamixer, Master, PCM, IEC958, and IEC958 D are all unmuted.

My last concern is one about KMix. KMix's help documents show an application that seems very helpful, with many tabs and sliders. I only have one tab ("HDA Intel") with a slider for Master and PCM. If I go to Settings->Configure Channels, I don't see anything about Headphones or Speakers. There's IEC958, IEC958 Default PCM, Capuure 1-3, and Input Source 1-3.

Please help!

---

### Post by tiagobt on 2009-05-31
Have you tried to unmute the **Surround** slider in KMix?

---

### Post by Clement_User on 2009-06-01
I can't find such a slider.
KMix, as I said, is very simplistic for me. It looks like this:
[IMG]http://i39.tinypic.com/2aoj2e.png[/IMG]
And the Settings->Configure Channels looks like this:
[IMG]http://i39.tinypic.com/28aq7x2.png[/IMG]

---

### Post by cyberdork33 on 2009-06-01
I think this is a documented issue with the iMacs. Unfortunately, I don't know that there is a fix (yet). 

if you want to see more sliders, use alsamixer. Check the FAQ.

---

### Post by Clement_User on 2009-06-01
Alsamixer through the terminal doesn't have any more sliders. Master, PCM, IEC958, and IEC958 D are all that are there. Are there perhaps some options I need to enable?

I'm not quite sure, but I think that when I "wubi"-ed Ubuntu, my speakers worked fine. Also, my friend also has an iMac (which is far older though), on which the headphone jack worked in Kubuntu, though he did use the Live CD instead.

---

### Post by tiagobt on 2009-06-01
> **Clement_User said:**
> Alsamixer through the terminal doesn't have any more sliders. Master, PCM, IEC958, and IEC958 D are all that are there. Are there perhaps some options I need to enable?

I'm not quite sure, but I think that when I "wubi"-ed Ubuntu, my speakers worked fine. Also, my friend also has an iMac (which is far older though), on which the headphone jack worked in Kubuntu, though he did use the Live CD instead.

I'm afraid your issue is different. KMix shows a slider called "Surround" in MacBook 2,1, but the iMac sound driver seems to behave differently.

---

### Post by Clement_User on 2009-06-01
Does this mean there's no hope? :(
Oh well. I'll live. Kubuntu's still really good. Though it could be even better. Hope it gets fixed soon!

Oh, if it helps any developers, I have an iMac 8,1.

---

### Post by cyberdork33 on 2009-06-02
> **Clement_User said:**
> Also, my friend also has an iMac (which is far older though), on which the headphone jack worked in Kubuntu, though he did use the Live CD instead.
Your friends Mac likely has different hardware and has already been "fixed". I also have an older iMac and everything works fine for me.

This may just be a mod that needs to be applied to the ALSA driver... You might check ALSA's bugtracker for something about this.

---

### Post by Clement_User on 2009-06-02
According to ALSA's documentation, 1.0.20 added support to iMac 24 Aluminum. It's listed under HDA codec driver here:
[http://www.alsa-project.org/main/index.php/Changes_v1.0.19_v1.0.20#HDA_Codec_driver](http://www.alsa-project.org/main/index.php/Changes_v1.0.19_v1.0.20#HDA_Codec_driver)

Would upgrading help? Does it look like something worthy of doing? If so, how would I go about doing it?

---

