---
title: "Sound from one source only (hda intel soundcard)"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by gidra on 2008-04-01
I'm a bit of a newbie as regards to hardware configuration. I'm running ubuntu on asus a3ac laptop which comes with an hda-intel soundcard. after going through a lot of hassle to make my headphone jacks work, now i cannot hear sound from more than one source simultaneously. If i'm playing Xmms i don't hear sound notifications from Emesene, if i'm watching a clip on youtube can't get any sound from Xmms (Please check that : your soundcard is configured properly etc etc. ). Any ideas please cause its really frustrating to have such a perfect system yet with such issues.

---

### Post by mick8985 on 2008-04-01
I'd like to help you but, not knowing what you have done while trying to get the jacks working, I don't know what state your sound system is in at all, are you using oss?

---

### Post by hyper_ch on 2008-04-01
if it's using oss you might want to install aoss and runn everthing through that (I do it with TS2, WoW, aMSN, ...)

---

### Post by gidra on 2008-04-01
I configured Device settings in xmms to use default Audio Device for alsa and everthing seems to be working fine, at least for the time being. btw all i did to solve the jack issue was adding the following line options snd-hda-intel model=z71v position_fix=1 to alsa base.

---

### Post by mick8985 on 2008-04-01
Is there any conflicts between any other programs, or is it just xmms + anything else?

---

### Post by gidra on 2008-04-01
actually it was emesene which sometimes sounds notifications and sometimes doesn't (after having configured xmms as explained above). everything seems to working fine right now, if i have some troubles again i'll keep you posted, thanks

---

