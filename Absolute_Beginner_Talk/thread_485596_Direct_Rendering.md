---
title: "Direct Rendering?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by margerine_12 on 2007-06-27
Hello everyone,

I have just ran the command "glxinfo" and for direct rendering, it came up as "no". Should I be concerned?

Also, this may help a bit. My card is an asus EAX1600pro 512mb

Thanks in advance

---

### Post by alienexplorers on 2007-06-27
gterminator@terminator-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

Sounds like your drivers are not properly installed.

---

### Post by steve-shinn on 2007-06-27
It's nothing to be concerned about per se, as most apllications will run fine ..... it just means that certain graphic applications (incl Beryl) will not work/work correctly ?

Have you installed the drivers for the card ? or tried the restricted drivers ?

---

### Post by margerine_12 on 2007-06-27
> **steve-shinn said:**
> It's nothing to be concerned about per se, as most apllications will run fine ..... it just means that certain graphic applications (incl Beryl) will not work/work correctly ?

Have you installed the drivers for the card ? or tried the restricted drivers ?

I have beryl running at the moment, without any visible lag, however, I will look into trying to find the driver.

---

### Post by Crafty Kisses on 2007-06-27
> **margerine_12 said:**
> Hello everyone,

I have just ran the command "glxinfo" and for direct rendering, it came up as "no". Should I be concerned?

Also, this may help a bit. My card is an asus EAX1600pro 512mb

Thanks in advance

You should try installing your drivers.

---

### Post by margerine_12 on 2007-06-27
I got the direct rendering to work. Thanks guys

**Edit:** It seems to be a problem with my xgl session

---

