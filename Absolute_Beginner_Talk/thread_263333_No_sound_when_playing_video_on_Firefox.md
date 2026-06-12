---
title: "No sound when playing video on Firefox"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by neogeek on 2006-09-23
I access You-tube several times to watch videos.

Sound comes on sometimes and sometimes it there is no sound at all.

I turned on all system sound but makes no difference.

[-o<

---

### Post by pay on 2006-09-23
Try```
sudo aptitude install flashplugin-nonfree
sudo update-flashplugin
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
```and then change```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```and close down firefox and try again.
Goodluck

---

### Post by The Soundophiliac on 2006-09-23
I get the following after trying that. The same as when using gedit from terminal. 
```
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.

```

---

### Post by pay on 2006-09-23
Sorry, I don't know what the problem is then.

---

