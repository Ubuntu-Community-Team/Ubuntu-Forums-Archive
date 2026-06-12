---
title: "no sound in newly installed linux"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by asthana on 2008-03-28
Hi i have installed ubuntu in my Lenovo Y410 laptop but there is no sound. Can anybody help. I have Realtek sound card.:confused:

---

### Post by wolfen69 on 2008-03-28
see this [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by DBrocks on 2008-03-28
Hey. Yea, thats a common error. Here's one of the fixes I've seen. 

[FONT=monospace]Edit: /etc/modprobe.d/alsa-base[/FONT]
 [FONT=monospace]Add: "options snd-hda-intel position_fix=1 model=3stack" to end of file (without quotations)
Reboot[/FONT]

Also, take a look at [THIS]("http://ubuntuforums.org/showthread.php?p=3796486#post3796486")

---

### Post by DBrocks on 2008-03-28
If all else fails: Try this also.


[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by unicynic on 2008-04-25
I also use this laptop. To enable sound, wifi, and bluetooth, press Fn+F1 to suspend to RAM. Then wake the notebook up. Sound, wifi, and bluetooth will be ok. Just press unmute, fn+f5, or fn+f6 to enable each.

---

