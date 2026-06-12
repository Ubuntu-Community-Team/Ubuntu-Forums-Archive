---
title: "Sound trouble. :( Need help!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by startdrowning on 2007-10-26
I have looked all over the forums for someone with a similar problem but have not been able to find anyone. I recently installed Ubuntu 7.04 on my Toshiba Satellite a105-s2101 and everything worked great instantly. After upgrading to 7,10 my sound went out completely. No system beeps or anything. I've set the soundcard found by the terminal as my default. When I open up alsamixer master volume has no bar and can not be changed. It has 00 at the bottom of the bar. PCM settings seem to work and can be changed but have not changed my problem at all. There is also no sound icon in the system tray. This is driving me crazy!! I really like Ubuntu, and these forums have been most helpful. However, if I can not get sound to work that is a real deal breaker. Thanks for the help !  :)

---

### Post by MegaJim on 2007-10-26
hi, please post the output of 

```
sudo lshw -C multimedia
```

---

### Post by startdrowning on 2007-10-26
*-multimedia            
       description: Audio device
       product: SB450 HDA Audio
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

---

### Post by MegaJim on 2007-10-26
It seems there is a known issue with Gutsy and the SB450:

[https://bugs.launchpad.net/bugs/88570](https://bugs.launchpad.net/bugs/88570)

---

### Post by startdrowning on 2007-10-26
Seemed to of found a fix for it. Says it is for feisty but it worked for my 7.10.
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)
Sound now works but I still don't have a mixer in the taskbar.
Thanks everyone for your help ! :-D

---

### Post by thiebaude on 2007-10-26
You can add Volumn Control to the top panel

---

