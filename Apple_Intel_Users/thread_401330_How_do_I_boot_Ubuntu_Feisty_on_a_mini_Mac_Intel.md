---
title: "How do I boot Ubuntu Feisty on a mini Mac Intel??"
date: 2007-04-04
forum: Apple Intel Users
---

### Post by darkmaster on 2007-04-04
I'm not getting it. I followed this guide:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
Wich is recommended in so many other posts. After the bootcamp thing, I insert the Live CD into the drive, restart the MAC but OSX runs as usual, the Live CD does not start!! Why? On a normal PC I just put the cd in the drive and at restart the Live starts.... What should I do to make the Live Boot?

---

### Post by cyberdork33 on 2007-04-04
Hold [ALT] during boot to bring up a menu of bootable devices.

---

### Post by darkmaster on 2007-04-04
> **cyberdork33 said:**
> Hold [ALT] during boot to bring up a menu of bootable devices.

Aaaahhhh! Very well. It worked, now I'm Booting feisty but... the keyboard does not work in the menù where I have to choose what to do with the live... dammit... is it normal? Now Linux is booting for install or run live is the first option aniway....

---

### Post by cyberdork33 on 2007-04-04
Yes various people report problems with the keyboard at bootup. Once it starts up it should be fine...


Every once in awhile it will actually work in that first menu. This problem persists for some people in Grub once ubuntu is installed.

---

### Post by darkmaster on 2007-04-04
> **cyberdork33 said:**
> Yes various people report problems with the keyboard at bootup. Once it starts up it should be fine...


Every once in awhile it will actually work in that first menu. This problem persists for some people in Grub once ubuntu is installed.

In fact after boot everything works ok. 3D is up and running. I'm not sure if the wireless card is ok. Do you know anything about it? I'm on a Mini Mac Intel intel core duo 2ghz processor. I bought it on Cristmass. 

If I'll have keyboard problems even on normal boot, how will I be able to choose wheter to boot Ubuntu or OSX?

---

### Post by cyberdork33 on 2007-04-04
> **darkmaster said:**
> In fact after boot everything works ok. 3D is up and running. I'm not sure if the wireless card is ok. Do you know anything about it? I'm on a Mini Mac Intel intel core duo 2ghz processor. I bought it on Cristmass. 

I am not sure which card is in your Mac Mini but I am willing to bet it is a Broadcom-based one, which will take some work to get it to work ala ndiswrapper. Try reading here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

It is specifically for the MacBook, but most is the same for every Mac.

> If I'll have keyboard problems even on normal boot, how will I be able to choose wheter to boot Ubuntu or OSX?

It does not effect the Mac device chooser, only grub. Also, did you install rEFIt? That will make things a bit easier.

---

### Post by darkmaster on 2007-04-05
Thanks a lot for your help. As for the wireless card, everything is OK, not a broadcom but a new Atheros. Feisty is really something! The Restricted Drivers manager was something everybody was waiting untill the first release of Ubuntu :) It's fantastic! Every hardware of the Mac Mini was detected immediatelly! Ubuntu is monstruously faster than OSX on my Mac!! And every single thing worked without any problem! I'm astonished. Feistry really mad an enormous jump ahead from edgy. Looks like another distro, really. It should have been an LTS :)

Multimedia is wonderfull too. I have no words. As for the Refit firmware, sure, I installed it :) And for now I'm having no problem with feisty... wonderfull also the fact that Beryl's in the repos allready... compiz is pratically nothing. If I had to activate desktop effects (Nice opyion aniway...), pratically, allmost nothing changed. I'm very happy with this distro :)

---

