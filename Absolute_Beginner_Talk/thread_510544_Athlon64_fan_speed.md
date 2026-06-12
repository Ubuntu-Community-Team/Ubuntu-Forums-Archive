---
title: "Athlon64 fan speed"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by dulence on 2007-07-26
Hello, I'm experiencing a slight annoyance here and I was hoping someone could help me.
The CPU fan is constantly at 100%, and as such is making a lot of noise. Cool'N'Quiet is enabled in bios, cpu frequency scaling is up and running ("ondemand" mode) and so far I've been getting the "Cool" part but I have yet to witness the "Quiet" part. First thing that came to mind is to install the drivers AMD is supplying at their site, however I noticed that drivers that came with the distribution (Fiesty) are up to date. While using Windows XP, the cpu fan is almost silent until I start an intensive 3D application. Only then it yanks the RPM up. Is there a way I can make my fan behave this way under Ubuntu?

Thanks in advance. :)

---

### Post by skymera on 2007-07-26
install lm-sensors to control the fans and do other sutff.

[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by dulence on 2007-07-27
pwmconfig did it! *Jumps with joy*
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

Thanks for the lm-sensors hint. :)

---

