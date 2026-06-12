---
title: "Sound Juicer &quot;Could not link pipeline&quot;"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-26
What's that mean and how do I fix it? AKA it won't extract.
It only does it on mp3.  It works fine on ogg.  What's wrong with it?

---

### Post by OU812 on 2006-07-27
Hmmm. I had that error a long time ago when I was running zenwalk. But the app was ripperx. I was using prepackaged slackware apps since it wasn't in zws repo. But I kept getting that error. So I installed ripperx from source and the error disappeared. Or this may help a bit more

[https://help.ubuntu.com/community/CDRipping#head-452073ae050f16886cc103fbbcc27963919f5724](https://help.ubuntu.com/community/CDRipping#head-452073ae050f16886cc103fbbcc27963919f5724)

john

---

### Post by Iandefor on 2006-07-27
It's missing an mp3 codec- Ubuntu won't install patent-encumbered stuff like that by default, because it paves the way for legal barriers to it's cost-free distribution. It is, however, pretty easy to set up. 

Make sure you have Universe and Multiverse enabled (Do so [here]("https://help.ubuntu.com/community/Repositories/Ubuntu")) and open up a terminal (Applications menu --> Accessories --> Terminal), and then run the command ```
sudo aptitude install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by knowmad on 2006-10-11
> **Iandefor said:**
> It's missing an mp3 codec- Ubuntu won't install patent-encumbered stuff like that by default, because it paves the way for legal barriers to it's cost-free distribution. It is, however, pretty easy to set up.

Hmm, I'm getting this error when trying to extract to a WAV under Dapper. I've installed the good, bad and ugly plugins including the multiverse packages. I tried to go back to Grip but cannot figure out where my CD device is located (`cdrecord -scanbus` only shows my ATA harddisks though Juicer is clearly able to interact with the drive as I can extract to Ogg format).


William


EDIT: I found my CD at /dev/hda (dmesg and [this article]("http://www-128.ibm.com/developerworks/linux/library/l-cdburn.html") at IBM was helpful). Grip is working to rip CDs once I installed cdda2wav. Still no luck with Sound Juicer.

---

