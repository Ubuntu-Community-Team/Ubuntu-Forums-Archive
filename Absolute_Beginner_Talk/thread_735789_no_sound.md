---
title: "no sound"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Ruhoo246 on 2008-03-26
I just recently installed ubuntu onto my laptop, it took me a few times to notice, but there isn't any sound at all.  Not even through the headphone port (which is on the left side if that matters or not).  

hopefully some of this information will help:

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8400000 irq 20

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


if it isn't obvious, i'm a complete noob at this... i've tried a few different things and none seem to work... sorry if this is a repeat.  Appreciate all the help I can get.

---

### Post by kpkeerthi on 2008-03-26
Did you try changing mixer settings in [alsamixer]("http://ubuntuforums.org/showpost.php?p=4583341&postcount=4") ?

---

### Post by superprash2003 on 2008-03-26
hope this works [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Ruhoo246 on 2008-03-26
neither of those seem to work... thanks though.

---

### Post by northern lights on 2008-03-26
It's gonna be a bitch for sure, but your best bet is one of the workarounds described in the [HDAIntelSoundHowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by Redptc on 2008-03-26
Have you done all the basics? I don't mean to suggest naivete but 'sound' in Ubuntu can be and is sometimes very elusive.

Have you checked the sound icon in the panel? It may be best to activate some sound from Rythmbox prior to testing. You can see it working digitally even though you don't hear anything. When you see it 'working' adjust the controls after clicking the icon. 

Still nothing? Right click and select 'Open Sound Control', be sure to wiggle each control especially master and PCM.

---

### Post by JAPrufrock on 2008-03-27
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by nothingspecial on 2008-03-27
This is how I got my sound working. Hope it helps.

1st - sudo apt-get install linux-backports-modules-generic

2nd - Follow this thread
[http://ubuntuforums.org/showthread.p...=toshiba+sound](http://ubuntuforums.org/showthread.p...=toshiba+sound)

IMPORTANT
These instructions were kindly posted when the latsest alsa was 1.0.15
Now the latest version is 1.0.16
If you download the latest alsa files and copy and paste the code in that thread, it won`t work. Make sure you change any line of code with 1.0.15 in it to 1.0.16

Hope it works

---

### Post by nothingspecial on 2008-03-27
Sorry bad link there. This should work - 
[http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound](http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound)

---

### Post by Ruhoo246 on 2008-04-12
sorry it took me so long to try them out. nothing seemed to work for me...

---

