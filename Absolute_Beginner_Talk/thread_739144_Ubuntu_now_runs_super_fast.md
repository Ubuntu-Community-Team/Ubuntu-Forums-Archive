---
title: "Ubuntu now runs super fast"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by malangaman on 2008-03-29
I wanted to boot without the log in screen since I am the only one who uses the pc. I went to System-> Administration-> Login Window, provided my password, chose the security tab and clicked Enable Automatic Login remembering to specify myself as the user to be automatically logged in.

At reboot I received the following message:

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

To my knowledge I have not downloaded any other settings managers. I am using Ubuntu 7.10.

The thing is: I love it. The machine runs faster and the settings are more visually appealing to me than the ones I had before. 

Does anyone know how I may keep these settings? I am afraid that if I reboot again, I may not be able to reproduce the ones I have received as a result of this "accident".

---

### Post by markekeller on 2008-03-29
I have no idea what is causing your "problem"; but I think it ought to stick - as long as you don't change anything - and occur each time you reboot your computer.  I've had similar startup errors before (only with rather disastrous results), and they occurred every time I logged in.

---

### Post by spydon on 2008-03-29
When I got that error message and rebooted it didn't show up again...

---

### Post by Nythain on 2008-03-29
that, is the most random and  incurable "problem" i've ever had the displeasure of encountering with ubuntu so far... and unfortunately i have no idea how to keep the gnome-settings daemon from loading automatically... maybe in gconf, or maybe in your rc's somewhere... im not to familiar with gnome as of yet

---

### Post by malangaman on 2008-03-29
Thanks for the replies thus far. I think it would be good to learn how to control this. Stopping the daemon from starting enhances performance? What is managing the desktop in its place? There have to be some console commands to see what is running on the machine. Can anyone direct us to the information?

---

### Post by chewearn on 2008-03-29
Check the bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/197759](https://bugs.launchpad.net/ubuntu/+bug/197759)

EDIT: this one seemed to have better analysis:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/197153](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/197153)

---

### Post by mcduck on 2008-03-29
> **malangaman said:**
> Thanks for the replies thus far. I think it would be good to learn how to control this. Stopping the daemon from starting enhances performance? What is managing the desktop in its place? There have to be some console commands to see what is running on the machine. Can anyone direct us to the information?

Stopping the settings daemon will not affect your performance in any noticeable way.

Instead, disabling the desktop effects and using the lighter GTK theme (the blue/grey on you are probably seeing now) might give you better performance.

When the gnome-settings-daemon works correctly it will load whatever theme you have selected. When it fails, you get the default blue/grey theme.

---

### Post by malangaman on 2008-03-29
This is a well documented bug. I have read the launchpad threads that were suggested by AstalaVista . Greater minds than mine are working on it. It appears to be intermittent and there was one comment about how to restore the daemon by console work in Xorg. I am not going to fool with that right now. Probably there will be a fix soon since it appears it is too common.

---

### Post by malangaman on 2008-03-29
I rebooted, my old settings returned as if nothing had happened. I going to try as suggested:

disabling the desktop effects and using the lighter GTK theme

---

### Post by monkspeed on 2008-03-29
yep, i've just tried the "simple" theme, it is definately faster.

:D

---

