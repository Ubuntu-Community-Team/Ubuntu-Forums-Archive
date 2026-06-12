---
title: "Missing sound card codec"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-09-08
Before, I was able to record audio through my mic using audacity. For some reason, I cannot record now.

After running ```
cat /proc/asound/card0/codec#0 | grep -i codec
```, what came out was ```
:~$ cat /proc/asound/card0/codec#0 | grep -i codec
cat: /proc/asound/card0/codec#0: No such file or directory

```

---

### Post by ORBiTrus on 2007-09-08
Basic steps, you may have taken them already:

1) Identify all items under /proc/asound/card0
2) Unmute the microphone, and set it's volume high (under playback).  If you hear stuff, there is not physical problem.
3) Ensure the microphone is set up as the capture device.

---

### Post by wersdaluv on 2007-09-08
> **ORBiTrus said:**
> Basic steps, you may have taken them already:

1) Identify all items under /proc/asound/card0
2) Unmute the microphone, and set it's volume high (under playback).  If you hear stuff, there is not physical problem.
3) Ensure the microphone is set up as the capture device.

Thanks for the reply. :KS

I attached a screenshot of my /proc/asound/card0. I am sorry but I do not know what those files and folders are for.

The microphone is not muted. Whenever I speak, I can hear my voice from my speaker.

Last, I do not know how to set my microphone as the capture device in audacity.

---

### Post by wersdaluv on 2007-09-08
I have a builit-in mic and an external microphone. See the screenshot for the list of capture devices that i can select.

I tried the two ALSA VIA 8235s. What came out when I tried to record with them was ```
Error while opening sound device: pleace check the input device settings and project sample rate.
```

---

### Post by ORBiTrus on 2007-09-08
First, congratulations on your choice of file manager.  I can't stand a filemanager without tabs.  I will admit, however, that pcmanfm is a weaklink compared to the almighty konqueror.

Second, you can choose the input device using alsamixer's capture page - there's others, but I forget them all - (in terminal, type alsamixer, switch to the capture page [F3 or F4?], and ensure that CAPTURE is written underneath the microphone - if not, hit the right arrow key as required then spacebar)

Perhaps it would be best to try recording some speech in Sound Recorder.  Audacity is slightly more complex than Sound Recorder, and fewer variables is a Good Thing.

P.S. I'm a lazy advice giver.  I've got Ubuntu installed upstairs, but I don't feel like getting off my personal Gentoo box.  I'm even to lazy to pop open a terminal and find out whether it is F3 or F4.

Edit: From the number of programs running in the system tray, and that you are using Ubuntu True (non a customized install), I'd guess you have a GB of RAM or more.  Lucky duck; [/me visits NCIX...damn, PC5300 is CHEAP now.  PC3200 still to expensive for my blood, though].

---

