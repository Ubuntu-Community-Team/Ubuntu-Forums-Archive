---
title: "Wine sound issue (error in terminal)"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by bigee1212 on 2007-05-20
Hey,

When I run "winecfg" and click the "audio" tab, I get the following in the terminal:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

```

any ideas? im trying to play starcraft.

---

### Post by knn on 2007-05-20
> **bigee1212 said:**
> Hey,

When I run "winecfg" and click the "audio" tab, I get the following in the terminal:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

```

any ideas? im trying to play starcraft.

Those are just warnings, they're normal. You don't need the jack library, just use alsa as the audio output. The other two are missing features, but I don't think Starcraft needs sound capture. In fact, Starcraft should work pretty well with Wine:
[wine appdb entry]("http://appdb.winehq.org/appview.php?iVersionId=149&iTestingId=11607")

---

### Post by swodah on 2007-05-23
BTW - Be sure to use correct Default Sample Rate for DirectSound settings. I had severe problem with ALSA Driver. The system jammed (playing the first sound in a loop) until I changed the sample rate to 44100Hz. Other settings work with what ever selection, but that one was critical...

---

### Post by mmendez on 2007-05-25
Damn I posted on the wrong tab

---

### Post by Enverex on 2007-05-25
See [http://ubuntuforums.org/showpost.php?p=2719129&postcount=4](http://ubuntuforums.org/showpost.php?p=2719129&postcount=4)

---

### Post by Stanko on 2007-07-12
i had a same problem today, and i've changed two things in wine conf, 
go to the audio tab,

LEAVE THE OSS
1. change Hardware Accelaration to EMULATION
2. (this one is not necessary but sometimes it is) change Sample Rate to 44100 

my starcraft is fully loaded with sound and everything :)

---

### Post by omegamormegil on 2007-07-16
Greetings.  I was having similar issues.  The previous post fixed me up almost all the way.  I wanted to add that I still didn't have sound until I actually started a game, and turned the volume up from the Starcraft menu.

---

