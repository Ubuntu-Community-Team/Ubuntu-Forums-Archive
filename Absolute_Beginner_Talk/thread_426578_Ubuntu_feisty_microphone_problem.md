---
title: "Ubuntu feisty microphone problem"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by miznatt on 2007-04-28
Hi there! I have a webcam that I've used on windows for years that supports audio and video; mic built-in. Linux detected the cam no problem and lets me use it to record/stream video and take snapshots, however I can't seem to get the microphone to pick up any sound. I have checked my volume settings to ensure all microphone options are enabled and unmuted. Please if anybody has any ideas post a reply =)

[Related info]

Product page: [http://digiblue.com/digital_blue/dmc2.html](http://digiblue.com/digital_blue/dmc2.html)

Terminal code for "lsusb":

```
Bus 001 Device 002: ID 04fc:504b Sunplus Technology Co., Ltd Aiptek, 1.3 mega PockerCam
```

---

### Post by miznatt on 2007-05-05
::bump::

---

### Post by rfs1970 on 2007-05-06
Hi There,

Take a look here: 
[http://ubuntuforums.org/showthread.php?t=434488](http://ubuntuforums.org/showthread.php?t=434488)

Maybe it could help.

r.

---

### Post by miznatt on 2007-05-06
No luck :(

---

### Post by rfs1970 on 2007-05-06
Hi There,

Did you check : [http://digiblue.com/customer-service/support/digitalblue/dmc2/issues/04.html](http://digiblue.com/customer-service/support/digitalblue/dmc2/issues/04.html) ??

As I could understand, your microphone is set to capture the audio from your sound board and
no from the microphone in your web cam...

Click twice at the speaker icon on your top panel, and then, at the menu of the new window,
click on File / Change Device...

Confirm if there is a third option available(/detected) apart from ALSA and OSS...

If yes, pick that one and try to make a new movie again.


r.

---

### Post by miznatt on 2007-05-07
ALSA and OSS are my only choice, none of which appear to work. If it even recorded the soundboard, wouldn't it pick up any music or sounds or anything? While testing for audio to be recorded, I tried to see if it picked up the internal sounds but nonetheless a loud static sound was the result... Seems hopeless lol, thanks so much for your continued efforts!

---

### Post by Tomosaur on 2007-05-07
I know you said you already checked, but I had a similar problem. I needed to enable and unmute the 'Microphone Capture' option in the volume controls. If you've already done this, feel free to ignore this post :)

---

