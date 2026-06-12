---
title: "iMac - microphone not working"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by tattrat on 2008-05-06
I am finding that the mic on my iMac 20" (early 2006) is not picking up any sound. 

There is a suspect message in the log (which I guess may be related):

```
May  6 18:29:19 iMac-ubuntu804 pulseaudio[6282]: alsa-util.c: Cannot find fallback mixer control "Mic".
```

Any help would be appreciated.

Cheers,

Brendan

iMac 20" (early 2006) HH 8.04

---

### Post by cyberdork33 on 2008-05-06
that error looks strange, but I would check alsamixer first. make sure the mic channel is not muted, and that the capture channel is also unmuted and turned up.

---

### Post by tattrat on 2008-05-07
I have discovered that the sound recorder is able to make a recording, but the quality and volume is low.

I then installed alsa mixer, and discovered that the recording levels were low. This allowed sound recorder to make a louder, but still poor quality recording. 

I have now tried again inSkype, which is why I want the mic to work,  but the sound quality is too low to allow a sensible conversation.

Any more ideas would greatfully appreciated.

Cheers.

---

### Post by tattrat on 2008-05-07
I have discovered that the sound recorder is able to make a recording, but the quality and volume is low.

I then installed alsa mixer, and discovered that the recording levels were low. This allowed sound recorder to make a louder, but still poor quality recording. 

I have now tried again inSkype, which is why I want the mic to work,  but the sound quality is too low to allow a sensible conversation.

Any more ideas would greatfully appreciated.

Cheers.

---

### Post by tattrat on 2008-05-07
A real call, to real person on skype has shown everything to be fine. The test call with the robot woman, showed all was not well but the real call is fine. I can live without decent quality in sound recorder - I never use it anyway!

---

