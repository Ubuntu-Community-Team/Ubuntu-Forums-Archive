---
title: "Broken updates....arrrrrgh!!!"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2007-09-22
I am not getting all my updates working and can't install anything anymore...

What does all this mean?.....I just want to install some applications, nothing fancy.

Here is a screenshot.....

jon@UbuntuStudio:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 lmms galan mx44 cheesetracker gnome-bin rezound kaconnect
  libgtk-canvas1 libsdl-gfx1.2-4 fftw2 spiralsynthmodular libgnome32
  ttf-dustin gnusound ardour-gtk lmms-common gnome-libs-data ecamegapedal om
  libart2 libdv-bin specimen libgnorbagtk0 qmidiroute gdk-imlib1 kluppe
  libscsynth1 qmidicontrol gcc-3.4-base horgand libphat0 ams libsynfigapp0
  libsdl-sound1.2 synfigstudio libsynfig0 libsdl-ttf2.0-0 libxml++2.6c2a
  qmidiarp qsampler solfege libgnomeui32 libdb3 qarecord sfftw2 libgdk-pixbuf2
  freewheeling imlib-base ardour-session-exchange gmorgan amsynth liborbit0
  gdk-imlib11 libgig3c2 soundstretch python-ecasound2.2 libgnomesupport0
  ecasound libclalsadrv1 libg2c0 supercollider sweep libsclang1 libfox1.4
  soundtracker liblscp libgnorba27 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ardour
The following NEW packages will be installed:
  ardour
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/4968kB of archives.
After unpacking 17.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ardour
Install these packages without verification [y/N]? y
(Reading database ... 138477 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jon@UbuntuStudio:~$

---

### Post by LowSky on 2007-09-22
?

thy this..?

```
sudo apt-get remove ardour
```

---

### Post by saintj0n on 2007-09-22
I tried that and it gives me the same output as above.

:guitar:
UBUNTU ROCKS!!!!

---

