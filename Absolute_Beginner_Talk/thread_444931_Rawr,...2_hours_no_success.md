---
title: "Rawr,...2 hours no success"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-05-15
I am still stuck on the first step of installing Steam.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam) is very helpful for a newbie but I am note even a newbie yet, i'm pre-newb.

It says this: > Now run wine without any parameters. When wine is run for the first time, it creates all necessary directories, including your fake C: drive, which is per default located in ~/.wine/drive_c.

And I have followed these directions [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Now it says this: > 2.2. Compiling Wine from CVS

Instead of using binaries, you may compile the latest source yourself. You may use WineCVS to compile Wine from CVS.

[http://winecvs.linux-gamers.net/](http://winecvs.linux-gamers.net/)

Needed apps, packages, libraries:
wget, fontconfig, freetype2, freetype2-devel, bison, flex, libjpeg, libjpeg-devel, libpng, libpng-devel, zlib, zlib-devel, xorg-x11-devel (resp. XFree86-devel), Mesa (resp. xorg-x11-Mesa, XFree86-Mesa), Mesa-devel (resp. xorg-x11-Mesa-devel, XFree86-Mesa-devel), freeglut, freeglut-devel

Debian or Ubuntu users can just use:
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

Change to the location where the WineCVS.sh is lying and start it with:

sh WineCVS.sh

The script downloads with wget a archiv defaults.tar.gz with the need install scripts. After that you should see its installation menu.

Select a profile ... follow the steps...

... done!

Compilation and installation successful.

And I try to do this > apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev  but I get this error: > E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


So I did this > sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev and got this error > E: Couldn't find package x-window-system-dev so I deleted the x-window-system-dev bit and it was successful.

So I assume that replaces the need to do this > apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev 

So I need to know exactly what and how to do this > Change to the location where the WineCVS.sh is lying and start it with:

sh WineCVS.sh

---

### Post by tarchy on 2007-05-15
I'm trying to install Steam by the way :$

---

### Post by tarchy on 2007-05-15
Bump

---

### Post by Matthaeus on 2007-05-15
Try adding the word   sudo   in front of the commands when you get a permission error - this might fix some of your later issues.

Eg sudo apt-get

cd is the change directory command.

Matthaeus.

---

### Post by sessine on 2007-05-15
If you have followed the directions at the link you quote ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)) then you should have Wine installed.  You then don't need to mess around with compiling from CVS and can move on to point 3.1 of the Steam FAQ.

---

### Post by rich.bradshaw on 2007-05-15
so you installed all the software except for x-windowsblahblahblah dev.

Well, that's what you need. 

try sudo apt-get install xserver-xorg-dev

---

