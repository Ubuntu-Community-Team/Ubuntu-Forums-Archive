---
title: "Permission denied - are you root?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by tehmanwhos0ldtheworld on 2007-11-22
im trying to do this 

Debian or Ubuntu users can just use:
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

and im getting this

E: &#913;&#948;&#973;&#957;&#945;&#964;&#959; &#964;&#959; &#940;&#957;&#959;&#953;&#947;&#956;&#945; &#964;&#959;&#965; &#945;&#961;&#967;&#949;&#943;&#959;&#965; &#954;&#955;&#949;&#953;&#948;&#974;&#956;&#945;&#964;&#959;&#962;(unable to open lock file) /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
panaret@panaret-desktop:~$ 


any suggestions plz?

---

### Post by Paul820 on 2007-11-22
Put sudo at the beginning of the command, example:
> sudo apt-get install

---

### Post by kellemes on 2007-11-22
> **tehmanwhos0ldtheworld said:**
> im trying to do this 

Debian or Ubuntu users can just use:
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

and im getting this

E: &#913;&#948;&#973;&#957;&#945;&#964;&#959; &#964;&#959; &#940;&#957;&#959;&#953;&#947;&#956;&#945; &#964;&#959;&#965; &#945;&#961;&#967;&#949;&#943;&#959;&#965; &#954;&#955;&#949;&#953;&#948;&#974;&#956;&#945;&#964;&#959;&#962;(unable to open lock file) /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
panaret@panaret-desktop:~$ 


any suggestions plz?

**sudo** apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

---

### Post by bapoumba on 2007-11-22
Pleas add **sudo **in front of the command.

---

### Post by Anicka on 2007-11-22
You need to write "sudo" infront of the command. You will be asked for you password, so just type it and hit enter. The cursor won't be blinking while you're typing, but don't worry.

---

### Post by TidusBlade on 2007-11-22
According to you, you typed this:
```
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev
```
Try adding sudo before the whole command then ;)

---

### Post by tehmanwhos0ldtheworld on 2007-11-22
thanx!now after the installation im getting this one E: &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#949;&#973;&#961;&#949;&#963;&#951; &#964;&#959;&#965; &#960;&#945;&#954;&#941;&#964;&#959;&#965;(unable to find packet) c-window-system-dev

---

### Post by tehmanwhos0ldtheworld on 2007-11-22
sorry mistyped ,its x-window-system-dev,not c

---

### Post by overdrank on 2007-11-22
> **tehmanwhos0ldtheworld said:**
> sorry mistyped ,its x-window-system-dev,not c

HI could you post the link to the "how to" you are following on what you are installing?

---

### Post by Anicka on 2007-11-22
In the repos I can only find x-window-system and x-window-system-core. Both are so called transitional packages, which means that they are no longer needed to have a working system, but was there to make it easier to upgrade from an older set-up. Is there any reason in particular for you to want that package?

Edit: Is it wine you're trying to install? [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine) It's easier to get it directly from ubuntu-repos. Just type "sudo apt-get install wine" and all the dependencies are automatically installed.

---

### Post by aysiu on 2007-11-22
You want *xorg*, not *x-window-system-core*

---

### Post by tehmanwhos0ldtheworld on 2007-11-22
this is what im trying to do 

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by tehmanwhos0ldtheworld on 2007-11-22
:confused:

---

