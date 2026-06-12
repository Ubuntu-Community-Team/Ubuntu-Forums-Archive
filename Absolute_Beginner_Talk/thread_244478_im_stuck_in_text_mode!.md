---
title: "im stuck in text mode!"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by piege on 2006-08-26
i'm new to this os... ive bin messing on it for 2-3 days and i dont know why (i think it's becaused i tried messing around with some settings i though armless but then again...) and now when i try to boot ubuntu after the brown ubuntu loading page i hear three suspicious beeps and then i get to a screen which tells me i could load windows x (probably because it isnt configured proprely) and im stuck in text mode and dont know what to do !!! help would be appreciated. BTW i'm pleasently surprised how fun ubuntu is atm !!!

---

### Post by v1ct0r on 2006-08-26
Can you post the error messages ?

---

### Post by piege on 2006-08-26
it just says that windows x won't load ...

---

### Post by Kobalt on 2006-08-26
Did this happen after a recent update that happened the 21st of this month ? If so, check [this page]("http://www.ubuntu.com/FixForUpgradeIssue") to know how to fix this. 
Otherwise, to repair your xorg configuration, type this command line : 
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the question and reboot, it should work. I hope so ! 

Cheerios !

---

### Post by kaamos on 2006-08-26
When in text mode, log in and use these commands to recover the default settings:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot

```

---

### Post by piege on 2006-08-26
well i just updated everything 2day for the first time since before that i had trouble with my wireless connection im going to try the command and get back to yall thanks a lot i'm amazed of the speed of the replies

---

### Post by piege on 2006-08-26
sudo dpkg-reconfigure xserver-xorg  says it's either broken or partially installed

and sudo dpkg-reconfigure-phigh xserver-xorg command not found

---

### Post by %hMa@?b&lt;C on 2006-08-26
sudo aptitude update 
sudo aptitude upgrade
startx
try that.
if the startx part doesnt work then
sudo dpkg-reconfigure xserver-xorg

---

### Post by derred on 2006-08-26
You can also try to first remove(complete remove) and then reinstall xorg. You can do this with apt-get remove package_name. Then delete the xorg packages you downloaded earlier (if any), and finally reinstall the xorg server. Hopefully this helps:wink:

---

### Post by piege on 2006-08-26
the start x thing doesnt work ...xinit:connection refused(errno111) and no such process(errno3)

and the thing on mondays update bug looks exacly like my screen but the troubleshooting doesnt work first the apt-get update tells me there are not updates available and then the install xserver-xorg-core tells me the exact same thing haven't tried removing the package do i just input sudo apt-get remove xorg?? and get sudo apt-get update get sudo apt-get upgrade sudo apt-get install xorg???

---

### Post by confused57 on 2006-08-26
Can you downgrade using?:

sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb


I've seen it mentioned in previous posts to downgrade without an internet connection.

---

