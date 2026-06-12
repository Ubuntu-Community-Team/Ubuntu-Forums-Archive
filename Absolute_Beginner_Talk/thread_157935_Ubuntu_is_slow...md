---
title: "Ubuntu is slow.."
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by gam3r on 2006-04-10
Hello, First of all hello my new linux friends!:cool: 

This is the first ever linux distro i've tried..i am impressed. I installed ubuntu on my old unused desktop PC(not the live version, if you ask) in hope i could revive it for some webbrowsing and light office work(i was hoping it would be faster than windows).

Here are my specs:
Celeron 800Mhz
376MB Ram
8MB On board graphics

I installed it fine, everything works(i think) but the problem is it's really slow...I don't think my processor or ram is holding it back, i think its the onboard graphics as when i minimize a window there is alot of ghosting and its slow. What can i do about this? Is there a lighter, good looking GUI which is easy to install for a noob?

Thank you, i hope you understand what im trying to tell you!

Me = n00b :D

Oh i almost forgot, Im trying to install automatix. I follwed the instructions in the thread on this forum, installed it and when i run it from system tools it requests a key from some website and fails(yes the machine has internet access). Why?

---

### Post by Darkriser on 2006-04-10
consider installing xfce4 desktop. either run sudo apt-get install xubuntu-desktop from console or install your system from scratch according this howto: [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

---

### Post by gam3r on 2006-04-10
hi, thanks for replying. When i do that in the terminal it says "couldnt find package xubuntu-desktop"....what to do?

Also do you have any idea how to install automatix?cant get past the key thing

---

### Post by TrendyDark on 2006-04-10
Yeah, very little video RAM would cause Ubuntu to be pretty slow compared to an older OS. Maybe you should try using XFCE or FluxBox

---

### Post by gam3r on 2006-04-10
Hi, how do i install xfce without xubuntu? i download the graphical installer but when i run it it tries to open it in geedit

---

### Post by erniewinner on 2006-04-10
i'm no expert but i'd say your graphics card is holding you back but not because of ram. a celery 800 is about 600mhz of a proper p3 (all things tolled.) and you ram is ok. unless you have some other unoptimised hardware someware... maybe a sound driver? anyway my point is my laptop has only 8 mb ram but yours is "onboard" any ideas on the chip??? maybe your experiance could be improved by a better £5 to £10 graphics off ebay... they are really that cheap. :rolleyes:

---

### Post by halfvolle melk on 2006-04-10
The xubuntu-desktop can be found in the **universe** repository. This repository needs to be enabled in  the file /etc/apt/sources.list. Here's how to do that:
[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto) (command line)
or
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) (graphical interface)

Once added you can run the command
```
sudo apt-get install xubuntu-desktop
```

---

### Post by gam3r on 2006-04-10
Hi, i did that and the download updates fail..im connected to the net and still...

---

### Post by Jimmey on 2006-04-10
What errors are you getting?

---

### Post by gam3r on 2006-04-10
basicaly i enable the univeral repo's and then it prompts me to update the lists. So i click yes and it gets stuck on download 5 of 11...i try removing some repositories and it the dl wont start it will just say downloading file 1 of 3...

---

### Post by halfvolle melk on 2006-04-10
Oops, sorry, I forgot something.

run this first:
```
sudo apt-get update
```
Aftr that you do the apt-get install thing.

---

### Post by gam3r on 2006-04-10
i did that, but it just stays at 0%  connecting.....


> sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.










---

### Post by fuscia on 2006-04-10
openbox and icewm are fast. fluxbox is fast, but not the version from synaptic. if you want to stay with gnome, try using bum (boot up manager) to turn off some of the unnecessary things running.

---

### Post by halfvolle melk on 2006-04-10
[QUOTE=gam3r]i did that, but it just stays at 0%  connecting.....[/QUOTE]
That's wierd. what does "cat /etc/apt/sources.list|grep universe" say?

Edit: Here you may find a universe repository that does work:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by gam3r on 2006-04-10
Ok..i got it to move along abit...somethings was wrong with my firefox as it would only resolve ipaddresses and not domain names i dunno why..

i did the
> sudo apt-get install xubuntu desktop
and this is the problem now
> 


keval@ubuntu:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  abiword abiword-common cdrdao gqview graveman gtk2-engines-xfce ivman
  libdbh1.0-1 libenchant1c2 libexo0.3-0 libgpgme11 libid3tag0 libmad0
  libmodplug0c2 liboggflac3 libsensors3 libxcomposite1 libxfce4mcs-client-2
  libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3 libxine1c2 mousepad
  rox-filer sox sylpheed sylpheed-i18n vorbis-tools xfcalendar xfce4
  xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin
  xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme xfce4-iconbox
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer
  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin
  xfce4-sensors-plugin xfce4-session xfce4-showdesktop-plugin
  xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager
  xfce4-terminal xfce4-toys xfce4-trigger-launcher xfce4-utils
  xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin
  xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4 xfwm4 xfwm4-themes
  xubuntu-artwork-usplash
Suggested packages:
  abiword-plugins abiword-plugins-gnome xpaint lm-sensors menu xine-ui jpilot
  sylpheed-doc xsensors a2ps psutils
Recommended packages:
  abiword-help libjpeg-progs gv metamail sylpheed-claws-scripts
The following NEW packages will be installed:
  abiword abiword-common cdrdao gqview graveman gtk2-engines-xfce ivman
  libdbh1.0-1 libenchant1c2 libexo0.3-0 libgpgme11 libid3tag0 libmad0
  libmodplug0c2 liboggflac3 libsensors3 libxcomposite1 libxfce4mcs-client-2
  libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3 libxine1c2 mousepad
  rox-filer sox sylpheed sylpheed-i18n vorbis-tools xfcalendar xfce4
  xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin
  xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme xfce4-iconbox
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer
  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin
  xfce4-sensors-plugin xfce4-session xfce4-showdesktop-plugin
  xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager
  xfce4-terminal xfce4-toys xfce4-trigger-launcher xfce4-utils
  xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin
  xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4 xfwm4 xfwm4-themes
  xubuntu-artwork-usplash xubuntu-desktop
0 upgraded, 72 newly installed, 0 to remove and 86 not upgraded.
Need to get 29.5MB/29.7MB of archives.
After unpacking 104MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libenchant1c2 abiword-common abiword gqview libid3tag0 libmad0 sox
  liboggflac3 vorbis-tools cdrdao graveman xfce4-icon-theme gtk2-engines-xfce
  ivman libdbh1.0-1 libxfce4util-1 libxfcegui4-3 libexo0.3-0 libgpgme11
  libmodplug0c2 libsensors3 libxcomposite1 libxfce4mcs-client-2
  libxfce4mcs-manager-2 mousepad rox-filer xfce4-panel xfce4-systray
  xfcalendar xfwm4 xfwm4-themes xfce4-mcs-manager xfce4-mcs-plugins
  xfce4-terminal xfce4-utils xfdesktop4 xffm4 xfce4-session xfce4
  xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin
  xfce4-genmon-plugin xfce4-minicmd-plugin xfce4-netload-plugin
  xfce4-notes-plugin xfce4-showdesktop-plugin xfce4-systemload-plugin
  xfce4-goodies xfce4-iconbox xfce4-mixer xfce4-panel-menu-plugin
  xfce4-sensors-plugin xfce4-taskbar-plugin xfce4-taskmanager xfce4-toys
  xfce4-trigger-launcher xfce4-wavelan-plugin xfce4-weather-plugin
  xfce4-windowlist-plugin xfce4-xkb-plugin xfmedia xfprint4
  xubuntu-artwork-usplash xubuntu-desktop
Install these packages without verification [y/N]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libxine1c2 1.0.1-1ubuntu10.2
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main libenchant1c2 1.1.6-1
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]


---

### Post by gam3r on 2006-04-10
Ahhhh igot it working now, its setup...well it says 
> Setting up xubuntu-desktop (1.4) ...


now its taken me back to the orignal prompt. Howdo i run xfce?

---

### Post by halfvolle melk on 2006-04-10
System -> log out -> log out

When loging on again, when it asks for the user name, you can choose a session. Choose XFCE.

---

### Post by gam3r on 2006-04-10
Thankyou all! it works and is much faster :D

Now another problem(sorry)...xfce wont let me browse my other hard drives which  are formated fat32/ntfs where as gnome would letme. How can i change this?

---

### Post by Darkriser on 2006-04-10
try looking here:
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

