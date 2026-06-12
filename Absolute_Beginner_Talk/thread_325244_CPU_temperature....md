---
title: "CPU temperature..."
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-12-25
Hi all,
Is there a software that can tell me stuff such as my CPU temperature, Fan speed and stuff like that, and be able to control them?(safely)
I notice that on ubuntu my laptop battery is emptied faaassstt!! lol any solutions for that?
thanks

---

### Post by scrooge_74 on 2006-12-25
> **Mazen said:**
> Hi all,
Is there a software that can tell me stuff such as my CPU temperature, Fan speed and stuff like that, and be able to control them?(safely)
I notice that on ubuntu my laptop battery is emptied faaassstt!! lol any solutions for that?
thanks

For the first question, check on the repositories and the applets that come with gnome you will find a few things.  The kernell in use has the ability to use hardware included with your motherboard to check on temp.

For the battery, you should check the power savings features in gnome, dim the screen, time to stop HD, etc.  Maybe your battery is just getting old and the only solution will be to get a new one in the long run.

---

### Post by Mazen on 2006-12-25
Well my battery isn't the best ever i know but when it comes to ubuntu it's really "short-lifed" and there aren't many options in the power managment....the only thing i found was "Prefer power saving over performance"!!!

---

### Post by scrooge_74 on 2006-12-25
My laptop has a few options to control the fan, the dimming of the screen, and a few other things.  You should check for your specific brand to see if you can find any options for linux

---

### Post by rajeev1204 on 2006-12-25
use the officially supported lm-sensors and sensorsd from the repositories 

then u also need to configure i2c kernel modules from source which u probably will get more info about from the site [www.lm-sensors.org](www.lm-sensors.org)

also using gdesklets application also from repos u can get it to display on ur desktop 

avoid i2c kernel module , instead try sensors-detect which is safer .more info from site.

a link to configure i2c module is somewhere in the forums .just search for lm sensors.

regards

rajeev

P.S the iam not sure about the i2c thing so read more before doing anything please.

---

### Post by Mazen on 2006-12-25
thanks i'll try that as soon as i hit home!!

---

### Post by msandoy on 2006-12-25
Regarding your original question, there is one program that I always use to monitor CPU usage, temperature and a whole lot of other stuff, just serach in synaptics package manager for gkrellm. This program also has a lot of plugins for almost everything you need to know about your computers hardware.

Since your battery has a very short life when running linux, open a console, and write top. This will display resources used, and if there is a program using more than 5% CPU when you are not doing anything with your computer, you have to check if you really ned this process.

---

