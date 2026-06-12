---
title: "First time user getting frustraited (searched with nothing)"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Satummoo on 2007-08-22
Hello, I am new to linux but would really like to get started.  I have no programing knowledge but am a medium/advance computer user as i've built many computers.  Right now, I have been reinstalling Ubuntu x64 about 3 times because I keep getting major problems.  The install goes very smoothly and so do the updates.  My first problem is video drivers.  I have an ATI 1950gt and instalation of the drivers is very annoying.  I've tried following the guides and the end result is during bootup (after ubuntu loads) I get a blank screen forcing me to completely reinstall ubuntu.  The only successfully way i've installed the drivers was to use ENVY which works alright but causes my auto updater not to work where I then copied some codes into the terminal and fixed it.  I don't like this method because i'm worried that it messes up some of the system files and doesn't allow me to use the graphic desktop feature.

My next problem is installing flash.  Firefox won't automatically install the plugins (because i'm running x64?) so I tried following some guides which did not work at all.  I know that linux/ubuntu has a steep learning curve but I know the end result will be well worth my time.  I've followed many of the ATI driver guides and they simply do not work for me.  If anyone can help me i'd very much appreciate it.

---

### Post by annda on 2007-08-22
sorry, no idea about ATI, but how about flash?

have you followed this?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
or some other guides?

in FF, type about:plugins (
EDIT: this is aboutCOLONplugins, not a smiley) in the address bar to see if you have a flash plugin installed - it might be there but not working properly... in that case, i'd suggest reinstall or even hardcore windows-style removing, rebooting, reinstalling.

---

### Post by kellemes on 2007-08-22
> **Satummoo said:**
> My first problem is video drivers.  I have an ATI 1950gt and instalation of the drivers is very annoying.  I've tried following the guides and the end result is during bootup (after ubuntu loads) I get a blank screen forcing me to completely reinstall ubuntu.

There never is reason to reinstall the hole system because you can't get the videodriver installed!
At least create a backup of your working /etc/X11/xorg.conf and remember what you did, so you can always get back into X, even if it's not with the preferred driver.

Try to post your /var/log/Xorg.0.log when X gives you crap.

---

### Post by Satummoo on 2007-08-22
> **kellemes said:**
> There never is reason to reinstall the hole system because you can't get the videodriver installed!
At least create a backup of your working /etc/X11/xorg.conf and remember what you did, so you can always get back into X, even if it's not with the preferred driver.

Try to post your /var/log/Xorg.0.log when X gives you crap.

no idea what that is or what that means :(

also checking the howto site on flash it gives instructions on repositories which I have no idea how to do that or what it means.  This seems way over my head.  I guess maybe I should read through everything or is there a quicker way? x64 firefox seems to be pretty unsupported.

---

### Post by mysticmatrix on 2007-08-22
ATI provides world renowned crap drivers when it comes to linux.

As for general info about Ubuntu, start from here. 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

This explains usual stuff like how to install software, what are repositories and other stuff.

---

### Post by bodhi.zazen on 2007-08-22
Well, you might want to stay with the 32-bit version of Ubuntu as you learn the ropes ...

---

