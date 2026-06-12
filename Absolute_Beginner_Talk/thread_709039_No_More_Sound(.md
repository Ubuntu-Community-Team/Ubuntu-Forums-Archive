---
title: "No More Sound:("
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by AlexOliver on 2008-02-27
I was playing some MP3s earlier today, and after updating to 7.1 I can no longer get sound out of my speakers. I have looked at some of the forums and tried a couple things and nothing has worked. I have a VT82C686 sound card (I Believe). Can someone help me please?
Thanks,
Alex

---

### Post by igknighted on 2008-02-27
> **AlexOliver said:**
> I was playing some MP3s earlier today, and after updating to 7.1 I can no longer get sound out of my speakers. I have looked at some of the forums and tried a couple things and nothing has worked. I have a VT82C686 sound card (I Believe). Can someone help me please?
Thanks,
Alex

The most common problem here is that the sound got muted.  Try running the command 'alsamixer' and seeing if any of the required channels are muted/low (front, pcm, master, etc.)

Failing that, try the command 'alsaconf' to reconfigure alsa.

---

### Post by northern lights on 2008-02-27
Failing that, post the output of ```
cat /proc/asound/cards
```

---

### Post by superprash2003 on 2008-02-27
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Crafty Kisses on 2008-02-27
> **AlexOliver said:**
> I was playing some MP3s earlier today, and after updating to 7.1 I can no longer get sound out of my speakers. I have looked at some of the forums and tried a couple things and nothing has worked. I have a VT82C686 sound card (I Believe). Can someone help me please?
Thanks,
Alex

Hmmm, post the following output:
```
lspci
```

---

### Post by igknighted on 2008-02-27
Almost forgot... the step by step sound troubleshooting guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by erginemr on 2008-02-27
Failing that still ;), you should try installing:
```
sudo aptitude install linux-backports-modules
```
to patch / update their ALSA drivers to the latest version.

---

