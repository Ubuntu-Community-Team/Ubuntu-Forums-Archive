---
title: "OO upgrade"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by jfl on 2006-04-27
I downloaded and installed Ubuntu 3 days ago.  Went very well ... 
However, the version I got of OpenOffice is 1.9.129 even though the splash says 2.0
The version I was using on Windoze was 2.0.2.
I enabled Universe, multiverse. etc. but the "Update Manager" shows nothing.

The reason I need the update is that I have transfered 52 spreadsheets to Ubuntu and, in the new version of OO Calc, if text is entered in a formula that expects a number it will be treated as 0 whereas in the old version it gives a #VALUE error.
Of course I can always put a "IF(ISTEXT(B25);0; my formula)", but it is going to take me all day and it is not really elegant. 

How do I upgrade *easily* ???  I checked Openoffice.org, didn't see anything about upgrading ... 
Please remember that my experience of Ubuntu is 3 days ... almost a veteran ;)

THANKS !!!

---

### Post by Jagot on 2006-04-27
Automatix is the easiest method:

[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by todoporron on 2006-04-27
Well, yes, I had the same question. I'm going to try automatix. Thanks a lot.

---

### Post by gingermark on 2006-04-27
Another method is to (in ubuntu) ```
gksudo gedit /etc/apt/sources.list
``` or in kubuntu to do ```
kdesu kate /etc/apt/sources.list
``` and add the following line to that file
```
deb http://people.ubuntu.com/~doko/OOo2/ ./
```
Save the file and then do ```
sudo apt-get update
``` and you should then be able to upgrade to 2.01 using apt or Synaptic / Adept

This way you can pick and choose what you want to install and what you want to leave out.

---

### Post by jfl on 2006-04-27
Thanks a lot !!!
Tried Automatix ... worked great !
Scared me because Ubuntu took a loooong time to reboot but its working.

THANKS AGAIN.

---

### Post by rajaiskandarshah on 2006-05-16
i did it differently:

1. download the oo.o pack from the website to my desktop (i download the version without java)
2. extract the pack
3. from the terminal, navigate to the rpms folder
4. from the terminal convert the .rpm files to .deb files: sudo alien *.rpm (you need to install alien from synaptic to do this)
5. from the terminal install the .deb files: sudo dpkg -i *.deb
6. from the terminal, navigate to the /rpms/desktop-integration folder
7. from the terminal, install the debian menus: sudo dpkg -i openoffice.org-debian-menus_2.0.0-3_all.deb
8. from the terminal, restart gnome-panel: killall gnome-panel (or just restart your computer if you are a pessimist like me)
9. from synaptic, remove the various openoffice.org2 packages with version 1.9.* (if not removed, version 1.9 will remain the default oo.o application) and (if you are a pessimist like me, it is a good idea to remove it one by one, eg openoffice.org2-writer which will automagically remove openoffice.org2).

it is very worthwhile to upgrade to the latest oo.o2 - loading is faster as compared to 1.9.* and as compared to oo.o2 on winxp. and less crashes and recovery works.

i'm still a n00b and the above is good practice for beginners on installing software from the terminal besides synaptic and apt-get. particularly for printer drivers which normally come in the CD (i'm using brother mfc7420 laser printer/fax/copier).

---

