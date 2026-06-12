---
title: "Sound Quality of MP3's"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Village on 2007-02-23
I'm using Amarok to play my MP3 collection which I transfered over with an iPod when I made the big jump to Kubuntu. 

Sadly I've noticed that there is now a level of distortion with the MP3 playback, this wasn't the case when I was using Windows to play the files. 

Any suggestions as to how to get back to my previously good sound quality. 

Village

---

### Post by SeanTater on 2007-02-23
try this:
```

sudo aptitude install mpg321
mpg321 /the/path/to/your/mp3s

```
See if it sounds any better

Also, try XMMS, Juk, and the numerous other media players if the above helps

---

### Post by Rhubarb on 2007-02-23
Try adjusting your mixer settings:
[http://www.ubuntuforums.org/showthread.php?t=333303](http://www.ubuntuforums.org/showthread.php?t=333303)

Or try playing the mp3 in vlc:
[http://www.ubuntuforums.org/showthread.php?t=346495](http://www.ubuntuforums.org/showthread.php?t=346495)

---

### Post by mcduck on 2007-02-23
Open sound mixer (Applications/Sound & Video/Volume Control) and make sure you don't have _all_ sliders at full volume. This will cause distortion & noise. Also check this for both Alsa & OSS (File/Change Device).

I usually keep everything else around 90% so I can fully use the range of PCM volume (controlled by buttons on my keyboard)

---

### Post by SeanTater on 2007-02-23
> **mcduck said:**
> Open sound mixer (Applications/Sound & Video/Volume Control) and make sure you don't have _all_ sliders at full volume. This will cause distortion & noise. Also check this for both Alsa & OSS (File/Change Device).

I usually keep everything else around 90% so I can fully use the range of PCM volume (controlled by buttons on my keyboard)

The reverse can also be a problem, speakers at ~100% and the mixer at ~2%.  I also keep mine at about 70-90% (mixer) and 20-30% (Speakers)

---

### Post by Village on 2007-02-26
Thanks for that folks, 

I tried playing around with the volume settings and the equalizer and it seemed to fix the problem. Thanks for your advice to all of you, 

A nice easy-to-fix problem!

Village

---

### Post by mahiyar on 2007-02-26
I have generally found that Ubuntu/Linux like in everything else gives more control in setting sounds, I prefer the finely tuned sound of my Ubuntu mp3 then windows.

---

