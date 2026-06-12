---
title: "Audacity no in or out sound"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Captaingracekidd on 2007-09-08
I get a message saying I have an error in sound in/output and will not be able to play or record. Installed alsa-oss as was showed in another thread and uncheched the ESD in sound but it still doesnt work.  I also tried to uncheck the box for systemsounds. Help.

---

### Post by GMachine_24 on 2007-09-11
Hi. You probably know this - but this is what used to happen to me (and still does). If I have another app that is using the sound card Audacity cannot record/play. Sometimes even if I've closed the other app Audacity still will not play until I log out and log back in.

Having said that, I'm sure there is some way to resolve this problem more elegantly - hopefully someone here will know. And, of course, your problem could be completely different. Just for what it might be worth.

--gm

---

### Post by tgalati4 on 2007-09-11
Close xmms or any other sound application.  Audacity uses OSS which locks the sound hardware to one application.  ALSA allows multiple devices to mix to the sound hardware.  Make sure you have the appropriate sound card selected in Audacity's preferences.

---

