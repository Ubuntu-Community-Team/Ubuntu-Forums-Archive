---
title: "Photoshop 7"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-12-03
Having installed wine from Synaptic package manager I'm attempting to install Photoshop 7 from a CD.  I do this by clicking on the setup.exe on the CD then two windows open, one the setup window which is the one which would normally show the installation progress and another which says 

"Setup Initialization Error"

"Setup is unable to find a hard disk loacation to store tempory files.
Make a least 3089KB free disk space available and then try running setup again"

What do I do next? Please be as specific as possible as I'm new to Ubuntu.

---

### Post by codejunkie on 2006-12-03
This might help install wine first preferably the latest version from [www.winehq.com](www.winehq.com) but the one in the repos should work fine then open a terminal and run ```
winecfg
``` this will configure wine and setup the fake windows partition. then open a terminal and cd to the directory contaning the photoshop setup files then run ```
wine setup.exe
```replace setup.exe with the actual .exe file to start the install you might also want to install the msttcorefonts package it will make the interface a little more pleasing you can find info on that **[HERE]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Extra_Fonts")**
hope this helps.

---

### Post by teet on 2006-12-03
> **a.v.l said:**
> Having installed wine from Synaptic package manager I'm attempting to install Photoshop 7 from a CD.  I do this by clicking on the setup.exe on the CD then two windows open, one the setup window which is the one which would normally show the installation progress and another which says 

"Setup Initialization Error"

"Setup is unable to find a hard disk loacation to store tempory files.
Make a least 3089KB free disk space available and then try running setup again"

What do I do next? Please be as specific as possible as I'm new to Ubuntu.

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

Check out wine tools.  That's what I used to install photoshop 7 in dapper drake.  I haven't tried it in edgy, but I figure it would work too.

-teet

---

### Post by orko3001 on 2007-09-02
Hi, I installed it under wine but get this error:

Unable to continue because of a hardware or system error. Sorry but this error is unrecoverable.

Thankyou for any advice

---

### Post by Daveth on 2007-09-02
did you patch the installshield? 

see

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

in the "install stuff" section. Makes me wonder if it installed properly under WINE. What WINE version are you running? - not that it matters as PS6 is platinum under most recent wine versions.

---

### Post by orko3001 on 2007-09-04
I have patched the install shield now but still no luck. I did install it on my work machine but can't remember what I did. I think I clicked on something in synaptic. It gave me another wine option and then I could install photoshop 7.

I'll have to see what it is called tomorrow.

Cheers.

---

### Post by orko3001 on 2007-09-04
Interestingly when I install on my home machine I get 'Error installing the shortcut set' which I didn't get on my work machine. I didn't take much notice of that before but could it be part of the problem? 

Cheers

---

### Post by orko3001 on 2007-09-04
I think it is a wine issue - how do I uninstall wine?

---

### Post by orko3001 on 2007-09-05
Wine Windows Emulator - I have wine doors on my home computer.

---

