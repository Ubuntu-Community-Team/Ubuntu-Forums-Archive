---
title: "mp3 help"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by supahdude on 2008-03-04
im new to ubuntu, i have gutsy gibbon 7.10, i cant figure out how to play my mp3's ive installed numerous programs/ codecs and still cant get it....

anyone have any suggestions

---

### Post by JoshuaRL on 2008-03-04
Go to Applications->Add/Remove

Then search for "restricted".

The package you want is called "Ubuntu Restricted Extras".  That should fix it for you.

---

### Post by ryanhaigh on 2008-03-04
```
sudo apt-get install ubuntu-restricted-extras
``` will install mp3 support as well as other codecs, flash and java +more.

---

### Post by taurus on 2008-03-04
Have you tried the ubuntu-restricted-extras package?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by kool_kat_os on 2008-03-04
> **JoshuaRL said:**
> Go to Applications->Add/Remove

Then search for "restricted".

The package you want is called "Ubuntu Restricted Extras".  That should fix it for you.

+1

---

### Post by supahdude on 2008-03-04
i already had that, i removed it then reinstalled it and i still cant play anything, i cant even play them in frostwire, any other suggestions guys?

---

### Post by JoshuaRL on 2008-03-04
What exactly are the issues?  Does sound not work, or does it show the error when you try to play?

---

### Post by supahdude on 2008-03-04
"Unknown playback error"

when i use the rythmbox music player
________________________________________

"failed to open audio output: OSS Driver 1.2.10"

with xmms
_____________________

"audio output unavailable; the device is busy.

xine parameters:"

with Amarok

---

### Post by ryanhaigh on 2008-03-04
Have you got any audio working at all?
Excellent timing!
Well looks as though its a sound configurtion issue

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

post back if you have any issues

---

### Post by oedha on 2008-03-04
> **supahdude said:**
> "Unknown playback error"

when i use the rythmbox music player
________________________________________

"failed to open audio output: OSS Driver 1.2.10"

with xmms
_____________________

"audio output unavailable; the device is busy.

xine parameters:"

with Amarok

seems like audio(hw)problem......

---

### Post by shacamin on 2008-03-04
I think Amarok has a really simple way of getting the codec. I just recently got a false error telling me that Amarok couldn't play .mp3's (it was the file), but it gave me the option of getting the codec for .mp3's. Try Amarok, and if that doesn't work, VLC should definitely work.

---

