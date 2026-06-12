---
title: "display help?"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by reddog on 2005-12-09
i installed ubuntu the first problem i had was hotplug subsystem wouldn't say ok.fixed that by pulling out my optical mouse and other usb devices.

now it says i have some sort of display issues like xserver or something like that then it says it will disable it until it works right i don't know whats goin on since im only about 3 days tryin to try out ubuntu but cant go any further than that can someone help?????? if it helps im using a geforce 5500 256 mb card please help i really want to learn linux

thanx for your time 

                                     reddog

---

### Post by bluefrog on 2005-12-09
u should be able to log in with a console (command line) using your user and password.

from the console type

sudo apt-get install build-essential
then once it's installed type
sudo dpkg-reconfigure xserver-xorg  (can't remember if it works without build-essential installed that's why I tell you to install build-essential, but u can try to reconfigure in the first place..)

Some questions qill be asked afterwards, defaults answer to each question should do the trick.

Follow it to the end (kind of long if not used to it).
U should have a graphical desktop afterwards.

Once there u can use applications > internet > xchat and connect to ubuntu server to talk on the internet irc channel and ask questions..

james

---

### Post by reddog on 2005-12-09
[QUOTE=bluefrog]u should be able to log in with a console (command line) using your user and password.

from the console type

sudo apt-get install build-essential
then once it's installed type
sudo dpkg-reconfigure xserver-xorg  (can't remember if it works without build-essential installed that's why I tell you to install build-essential, but u can try to reconfigure in the first place..)

Some questions qill be asked afterwards, defaults answer to each question should do the trick.

Follow it to the end (kind of long if not used to it).
U should have a graphical desktop afterwards.

Once there u can use applications > internet > xchat and connect to ubuntu server to talk on the internet irc channel and ask questions..

james[/QUOTE]


ok i did that and now here's everything that it said

reading package lists... done
building dependency tree... done
e: couldn't find package build

package 'xserver-xorg'is not installed and no info is available
use dpkg --info (= dpkg-deb --info)to examine files
and dpkg --contents (=dpkg-deb --contents)to list their contents
/usr/sbin/dpkg-reconfigure:xserver-xorg is not installed
  
now im stuck again please help me

and dpkg --cont

---

### Post by steve.horsley on 2005-12-09
Try **sudo apt-get install xserver-xorg**. This will probably want the installer CD in the drive.

---

