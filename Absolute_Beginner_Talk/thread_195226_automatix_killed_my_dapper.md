---
title: "automatix killed my dapper"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-06-12
I just ran automatix installing a bunch of stuff like nvidia drivers, frostwire, and such. On the first reboot, the logon screen came up with a white background and is frozen. What do I do now?:confused:

---

### Post by Ben Sprinkle on 2006-06-12
restart lol again if no work just er dunno lol sorry

---

### Post by rubrboots on 2006-06-12
wow restart my computer, I would of never thought of that on my own. Thanks for the help:rolleyes:

---

### Post by Ben Sprinkle on 2006-06-12
ur welcome i feel smart now :cool:

---

### Post by rubrboots on 2006-06-12
Any other suggestions out there?

---

### Post by Ben Sprinkle on 2006-06-12
yea re install ubuntu lol:-({|=

---

### Post by arendm on 2006-06-12
I tried Automatix once but never again. Best thing to do is re-install indeed and after that, if you want to install things take a look here 

[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")

or here

[http://lunapark6.com/?p=1235](http://lunapark6.com/?p=1235)

It's better to install things yourself so you know what's going on and learn something ;)

---

### Post by xael on 2006-06-12
[QUOTE=arendm]I tried Automatix once but never again. Best thing to do is re-install indeed and after that, if you want to install things take a look here 

[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")

or here

[http://lunapark6.com/?p=1235](http://lunapark6.com/?p=1235)

It's better to install things yourself so you know what's going on and learn something ;)[/QUOTE]

Did you try a beta release of Automatix?. Probably it was a minor bug in there, the final version hardly ever fails.

---

### Post by echo $USER on 2006-06-12
Did you back up your xorg.conf before installing the nvidia driver?  If so revert to your backup, and possibly your GUI will follow.

---

### Post by catlett on 2006-06-12
It's probably just your video drivers. It sounds like you can't get into ubuntu so choose ubuntu "recovery mode". This will give you a root login enter ```
dpkg-reconfigure xserver-xorg
``` This will run you through the x configuration. Just let the computer auto select. It did fine the first time so it should do fine now. The main thing is to make sure it doesn't choose nvidia as a driver. nv is fine or vesa. It will ask to write the configuration to file and when you restart it will use that configuration.
Hopefully it was the nvidia driver install and the dpkg- selected driver willl work.

---

### Post by confused57 on 2006-06-12
Yes, it's probably your nvidia driver...if changing that doesn't work, you can try removing some of the packages you installed with Automatix(after booting into recovery mode):

[http://www.ubuntuforums.org/showthread.php?t=90797](http://www.ubuntuforums.org/showthread.php?t=90797)

Automatix has always worked great for me on 3 different computers, I just don't install too much at one time...a couple of things at a time.

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=arendm]I tried Automatix once but never again. Best thing to do is re-install indeed and after that, if you want to install things take a look here 

[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")

or here

[http://lunapark6.com/?p=1235](http://lunapark6.com/?p=1235)

It's better to install things yourself so you know what's going on and learn something ;)[/QUOTE]


I tend to agree. I used another "idea" posted here and it has caused all sorts of problems that I need to manually uninstall it.

The only software one can trust is that from synaptic.

---

### Post by tseliot on 2006-06-13
Automatix installs the driver which is in the Ubuntu's repos. And BTW it didn't "kill" anything.

It might be a hardware incompatibility or something went wrong during the installation.

I need to know the model of the graphic card

---

