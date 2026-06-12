---
title: "Screen Saver Not Displaying"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-01-18
I am selecting a screen saver in Gutsy 7.10 but when its time for the saver to work my screen just goes black. Any ideas?

Thanks!

---

### Post by smurphy_it on 2008-01-18
Under power management, it might be set after x amount of minutes to blank the screen.  Try decreasing your timeout to say 2 minutes for example, and then see if your screensaver enables.

---

### Post by NilsE on 2008-01-18
For the life of me I can't remember where it is (probably in the configuration editor under gname-power-management)  but there is an option to go blank only  if on batteries and only execute the actual screensaver if on power.  Screensavers take a lot of processing so it saves the battery.

---

### Post by zakirs on 2008-01-18
system>pref>power management

in this search of" switch off the screen"

---

### Post by k8fox1 on 2008-01-19
This is is happening on my desktop system too. Blank screen is set to "never" in the power management. Ideas??

Thanks!

---

### Post by NilsE on 2008-01-19
Try this

Go into Configuration Editor and locate apps>gnome-screensaver and make sure mode is set to single and not blank.

---

### Post by Sinkingships7 on 2008-01-19
some screen savers in ubuntu won't work without at least some amount of graphics memory. do you have graphics card or onboard graphics? is so, what kind?

---

### Post by k8fox1 on 2008-01-21
Thats probably the problem. I am just using the Brookdale-G]GE Chipset Integrated Graphics card that came with the system. It did however come with an ATI 16mb Rage 128 DVI Video Card which I couldn't get working in Gutsy, 

-Mike

---

