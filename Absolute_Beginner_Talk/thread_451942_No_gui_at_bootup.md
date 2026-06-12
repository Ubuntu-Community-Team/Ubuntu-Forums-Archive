---
title: "No gui at bootup?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by ng30345 on 2007-05-22
Many attempts and have finally gotten the 6x alternate cd to install.  None of the others would install.  Now that I'm here, when I boot up, I dont get a gui, I get a lot of text that finally asks for my user/pass.  Once that is authenticated, it just shows me a dos-like prompt and is awaiting me to type in some mystical command, probably torturing me for falling asleep yet again in BASIC class way back in the day.  So, what genius thing have I done this time that is causing this to not boot up w/ a gui?  Thanks  (and please, don't tell my BASIC professor from college in 1984, he'd just get all pissed off at me again.)

---

### Post by Martin on 2007-05-22
Some details about the system you're trying to get working would be useful. If you don't know the specifis, the  manufacturer and model name should suffice.

---

### Post by louieb on 2007-05-22
6.x what that narrows it down to 14 different CDs'. Did the install CD have a GUI? Sounds like you did a server install from one of the alternate CDs'.

---

### Post by ng30345 on 2007-05-23
ubuntu-6.06.1-alternate-i386.iso is the file I installed.  Was this a server version?  I certainly didnt intend to install a server version.

---

### Post by ng30345 on 2007-05-23
It's an eMachines desktop.  Less than a 300Mhz processor and maybe 64M ram.  13G hard drive.  Very old.

---

### Post by oilchangeguy on 2007-05-23
> **ng30345 said:**
> It's an eMachines desktop.  Less than a 300Mhz processor and maybe 64M ram.  13G hard drive.  Very old.

is there anyway you can add more ram? you may need to try puppy linux, or damn small linux. with those low specs, i don't think you'll be able to get ubuntu to run properly.

---

### Post by louieb on 2007-05-23
> **oilchangeguy said:**
> ...puppy linux, or damn small linux ... i don't think you'll be able to get ubuntu to run...
I agree. If you need a GUI  Win95 might work too. Had Win98 on a 64MB machine. You can get a GUI with one of the lighter Linux distros. Add Slackware to the 2 above. Just for grins log in and type  ```
free -m
``` that will tell you how much memory the old PC has.

---

### Post by apunc1 on 2007-05-23
doesn't sound like you installed the server version 
for spits and giggles could you enter

```
startx
```

at the prompt and see if you get a gui

those are really low specs. have you tried puppy linux? you don't have to install it if you don't want. it runs really fast off of ram.

---

