---
title: "installed feisty - mic stopped working"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by lumarh on 2007-04-23
and i cant get it to work?

i can hear the mic through speakers but no record function (eg skype) is working, recording level monitor shows no response.

i had it working pre-upgrade. i have mucked around in alsamixer to no avail.. help??!!

---

### Post by lumarh on 2007-04-23
bump

---

### Post by Falcorian on 2007-04-23
I just got my mic working for recording in Edgy, maybe it's the same process?

I double clicked on Volume Applet (it's the volume control on your panel) and went Edit > Preferences. There I made sure '**Microphone**', '**Microphone Capture**', '**Mic Boost (+20dB)**', and '**Mic Select**' were checked.

After that a **Capture** tab appeared on the volume control panel, I selected this and made sure nothing was muted (no red x), then click the new **Switches** tab, turned off '**Line-In Capture**' and turned on '**Microphon Capture**'. You may or may not need to turn on Boost in that same tab.


That's how I got mine working, hope it helps you.

---

### Post by morpheus01 on 2007-05-11
Thanks for that brother Falcorian, it works great.

This'll be obvious to many of you but remember to close Skype and restart alsa before you test call again. 

```
sudo /etc/init.d/alsa-utils restart
```
Also the preference options are slightly different in Feisty - I just ticked everything, boosted the "capture mux" clicked on the "recording tab" unmuted "Capture" and boosted it up some.

If these settings were defaults during installation surely we'd be getting less posts about this every week?

(for any amateurs like myself you can get the sound icon by right clicking on your panel and choosing  "add to panel").

---

### Post by euchrid on 2007-06-07
In case the above doesn't work (it didn't for me), try updating the Alsa drivers. Instructions and information here:
[http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

---

### Post by Scotty562 on 2007-08-19
Didn't work for me :(. HP dv6500t

---

