---
title: "[SOLVED] Need Help"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by DIEB4ME on 2007-11-11
Ok im really new to ubuntu. I installed ubuntu 7.10, everything worked just fine untill it prompted me to update my graphics driver. I installed the new driver then restarted my comp, and now it will not finish booting the system and i get a command prompt with four or five lines of code. Does anyone know what im talking about, if so please help!

---

### Post by LaRoza on 2007-11-11
What is your graphics card, which driver did you use (now and before) and what are the lines of code you see.

---

### Post by samb0057 on 2007-11-11
if you can remember what driver you installed, remove it by typing sudo apt-get remove <drivername>, then the system should revert back to the old driver.

---

### Post by DIEB4ME on 2007-11-11
Ok i forgot what driver i installed. My graphics card is a nvidia geforce fx 5200 and my current xp driver is the 163.75 release.
This is what it says in the command prompt:
Starting anar(h) ronsiticcron anacron            [OK]
Starting deferred execution schedualer atd  [OK]
Starting periodic command schedualer crond [OK]
Checking Battery State....
Running local boot scripts (retc/rc.local)        [OK]

Then it just stays like that and does nothing, but i can still type stuff in the command line so my computers not fozen. I dunno if this helps at all but i am also dual booting xp with ubuntu.

---

### Post by samb0057 on 2007-11-13
Ok try this. type "dkpg-reconfigure xserver-xorg". If it asks for a driver, select "vesa" or "generic" or something like that. This should bring back the old driver. Sorry I can't be of more help I really don't know much about these things.

---

### Post by DIEB4ME on 2007-11-13
Ok I fixed it, Thanks for all of the help.

---

### Post by Inxsible on 2007-11-13
> **DIEB4ME said:**
> Ok I fixed it, Thanks for all of the help. Cool. Mark your thread as solved. Thread Tools>> Mark Thread as solved. :D

---

