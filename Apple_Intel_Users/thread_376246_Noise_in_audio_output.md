---
title: "Noise in audio output"
date: 2007-03-04
forum: Apple Intel Users
---

### Post by garlito on 2007-03-04
Hi,
I go on with my sound problems. When I play the test sound in the gstreamer properties window there is too much noise, it only disappears when I turn the volume down, but then I can hardly hear anything. This white noise is especially annoying in speech.

Does anyone have this problem? If not, what version of Ubuntu are you using? I'm still in Dapper.

Thanks in advance.

Edit: I forgot to mention I'm talking about an Intel Mac Mini

---

### Post by incubus on 2007-03-04
garlito,

I also get that on a Macbook, running Ubuntu Feisty.  It seems to be better than what you're saying, but it's basically the same problem.  At high levels, there's "white" noise.  I heard some people saying it's related to ALSA.  Others point to tweaking alsamixer.

Is this a relatively new Mac Mini you got?

incubus

---

### Post by ketilkn on 2007-03-05
Same issue here. Brand new Mac Mini. I am currently running Edgy. Feisty has the same issue.

---

### Post by garlito on 2007-03-05
I've read about a patch written perhaps by the mactel boys, sigmatel_audio.patch, but I don't know if it is already in use in Ubuntu kernels, I guess it isn't. Any way I haven't seen our problem reported, so no idea whether it could be a solution or not.

It seems to be necessary for the digital output to work, I personally only use a normal analogue headphones.

If any of you try this please report. I still must to have a look at the mactel web:

[http://www.mactel-linux.org/wiki/Main_Page]("http://www.mactel-linux.org/wiki/Main_Page")

---

### Post by dzoner on 2007-06-23
It seems that this problem afects all mac mini's ppc and intel.

I have mac mini with ppc and feisty, everything is working great except that white noise in sound.

---

### Post by tchorix on 2007-06-24
Same here. I have a MacBook Pro 15" con Ubuntu Feisty.

Tch

---

### Post by ronocdh on 2007-06-24
> **tchorix said:**
> Same here. I have a MacBook Pro 15" con Ubuntu Feisty.

Tch
I believe I experienced something similar (MBP 15"). To solve, I right-clicked on the audio icon in the tray and went to Open Volume Control. Then I clicked to the second tab and unchecked a box, though I'm sorry I've forgotten the name. It was the only option on that tab, IIRC. HTH, please post back.

---

### Post by tchorix on 2007-06-26
> **ronocdh said:**
> I believe I experienced something similar (MBP 15"). To solve, I right-clicked on the audio icon in the tray and went to Open Volume Control. Then I clicked to the second tab and unchecked a box, though I'm sorry I've forgotten the name. It was the only option on that tab, IIRC. HTH, please post back.

Thanks for the tip :) But actually, the problem is only considerable doing the sound test. Listening to music for instance, the noise rarely appears... only in a couple of songs with instruments with very high frequencies. The problem is a little bit higher with Amarok than with XMMS.

cheers
Tch

---

