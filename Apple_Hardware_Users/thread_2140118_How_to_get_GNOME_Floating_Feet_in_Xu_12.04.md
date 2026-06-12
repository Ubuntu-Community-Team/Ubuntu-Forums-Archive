---
title: "How to get GNOME Floating Feet in Xu 12.04???"
date: 2013-04-28
forum: Apple Hardware Users
---

### Post by este.el.paz on 2013-04-28
Folks:

Just installed Xu 12.04 64 bit in my '09 MBPro, defecting from almost a year of LM13, due to an erratic cursor problem that couldn't be solved w/o turning off the touchpad . . . and of course it's basically the same system . . . .  But, one thing that I seriously enjoyed in MATE was the GNOME Floating Feet screensaver . . . .  I posted a question awhile back when I installed Cinnamon DE, and the Floating Feet were shockingly . . . gone, but didn't seem possible to get them there so I went back to using MATE just to have those GNOME feet.

Today I installed "gnome-screensaver" . . . but didn't notice anything different in Screensaver in a Xubuntu session, haven't checked LXDE yet.  I'm wondering if there is a way to get the Floating Feet screensaver, short of trying to install the MATE DE package???  I went to gnome-look.org, but couldn't find it there.

I needs de feets, can anybody hep me?

e.e.p.

---

### Post by este.el.paz on 2013-04-29
Still hoping to get some direction on the Floating Feet . . . still trying to avoid the bloat of installing MATE, unless I have to.  Went to the GNOME web site to try to find the Feet screensaver, but it doesn't seem to be there.  Even found an online hack where somebody took the "Ubuntu floating logo" and turned it into floating race cars, but he obviously had the "Floating Logo" image already installed, don't know if I just wrote a copy of the file if that would install the GNOME logo Floating Feet . . . .  I'd just like to find the screensaver w/o the whole DE . . . any ideas?

e.e.p.

---

### Post by este.el.paz on 2013-04-30
Folks:

Based upon the amount of replies I'm assuming"It's not easy to get the Feets"??  So, I tried to install the MATE DE, but it didn't work, so I figured out that I don't have the LM sources.list to mine the MATE DE . . . .  Checking my present sources.list in nano shows:

```
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

```

which doesn't seem too extensive; still looking to get the Floating Feet screensaver, but trying to keep the sources.list as simple as possible, I search Google for LM13 sources.list, would there be any harm to adding the whole list pasted below, or just pick one or two?  The goal being to try to add the MATE DE and thereby get the FF screensaver . . . not really wanting to get into a MInt system, but particularly not wanting to mess up the Xu system . . . there was an issue with erratic cursor movement that would erase data that was happening in the LM system and I'm still trying to test to see if it's gone by going to Xubuntu based system . . . but I'd really like to get those Feet Floating across my screen if possible to do without making problems.

```
deb http://packages.linuxmint.com/ maya main upstream import
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ precise partner
deb http://packages.medibuntu.org/ precise free non-free

# deb http://archive.getdeb.net/ubuntu precise-getdeb apps
# deb http://archive.getdeb.net/ubuntu precise-getdeb games
```

Thanks for any knowledge that can be shared,

e.e.p.

---

### Post by matt_symes on 2013-05-03
Hi

I have been having a look at this. 

The "floating feet" screensaver is in the package mate-screensaver and that is in the repository..

> deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) maya main upstream import

The standard screensaver package that comes with Xubuntu is called xscreensaver. 

```
matthew-S206:/home/matthew % dpkg -l xscreensaver
zsh: correct 'xscreensaver' to '.xscreensaver' [nyae]? n
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-============================================================
ii  xscreensaver                5.15-2ubuntu1      amd64              Automatic screensaver for X
matthew-S206:/home/matthew %
```

This does not contain the "floating feet"" screensaver - and has not for a while. I could not see if in any of the xscreensaver packages.

```
matthew-S206:/home/matthew % apt-cache search ^xscreensaver
kscreensaver-xsavers - xscreensaver support for KScreenSaver
xscreensaver - Automatic screensaver for X
xscreensaver-data - data files to be shared among screensaver frontends
xscreensaver-data-extra - data files to be shared among screensaver frontends
xscreensaver-gl - GL(Mesa) screen hacks for xscreensaver
xscreensaver-gl-extra - GL(Mesa) screen hacks for xscreensaver
xscreensaver-screensaver-bsod - BSOD hack from XScreenSaver
xscreensaver-screensaver-dizzy - Graphics demo that makes you dizzy (XScreenSaver hack)
xscreensaver-screensaver-webcollage - Webcollage hack from XScreenSaver
matthew-S206:/home/matthew % 
```


You could add that repository to your sources, update and install it, however look what it will pull in - just for the "floating feet" screen saver.

This is the simulated run i did....

```

Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  caja caja-common fuse-utils libcaja-extension libcanberra-gtk-module
  libcanberra-gtk0 libdevmapper-event1.02.1 libfam0 liblvm2app2.2 libmarco
  libmate libmate-common libmatecanvas libmatecomponent libmatecomponentui
  libmateconf libmatecorba libmatedesktop libmatekbd libmatekeyring
  libmatemenu libmatenotify libmatepanelapplet libmatepolkit libmatevfs
  libmateweather libmateweather-common libsgutils2-2 libtasn1-3-bin marco
  marco-common mate-conf mate-conf-common mate-corba mate-desktop
  mate-desktop-common mate-dialogs mate-icon-theme mate-keyring mate-menus
  mate-mime-data mate-panel mate-panel-common mate-polkit mate-power-manager
  mate-power-manager-common mate-session-manager mate-settings-daemon
  mate-settings-daemon-common mate-settings-daemon-gstreamer mate-vfs
  mate-vfs-common mate-window-manager menu-xdg udisks
Suggested packages:
  fam sg3-utils rss-glx xfsprogs reiserfsprogs mdadm
The following NEW packages will be installed
  caja caja-common fuse-utils libcaja-extension libcanberra-gtk-module
  libcanberra-gtk0 libdevmapper-event1.02.1 libfam0 liblvm2app2.2 libmarco
  libmate libmate-common libmatecanvas libmatecomponent libmatecomponentui
  libmateconf libmatecorba libmatedesktop libmatekbd libmatekeyring
  libmatemenu libmatenotify libmatepanelapplet libmatepolkit libmatevfs
  libmateweather libmateweather-common libsgutils2-2 libtasn1-3-bin marco
  marco-common mate-conf mate-conf-common mate-corba mate-desktop
  mate-desktop-common mate-dialogs mate-icon-theme mate-keyring mate-menus
  mate-mime-data mate-panel mate-panel-common mate-polkit mate-power-manager
  mate-power-manager-common mate-screensaver mate-session-manager
  mate-settings-daemon mate-settings-daemon-common
  mate-settings-daemon-gstreamer mate-vfs mate-vfs-common mate-window-manager
  menu-xdg udisks
0 upgraded, 56 newly installed, 0 to remove and 0 not upgraded.
Inst libcanberra-gtk0 (0.30-0ubuntu2 Ubuntu:13.10/saucy [amd64])
Inst libdevmapper-event1.02.1 (2:1.02.74-6ubuntu4 Ubuntu:13.10/saucy [amd64])
Inst liblvm2app2.2 (2.02.95-6ubuntu4 Ubuntu:13.10/saucy [amd64])
Inst libmatecorba (1.2.2-3~precise linuxmint:13/maya [amd64])
Inst libmateconf (1.2.1-1~precise linuxmint:13/maya [amd64])
Inst libcaja-extension (1.2.1-1+precise linuxmint:13/maya [amd64])
Inst libmatedesktop (1.2.0-3+precise linuxmint:13/maya [amd64])
Inst libfam0 (2.7.0-17 Ubuntu:13.10/saucy [amd64])
Inst libmatevfs (1.2.1-2~precise linuxmint:13/maya [amd64])
Inst mate-vfs-common (1.2.1-2~precise linuxmint:13/maya [all])
Inst fuse-utils (2.9.0-1ubuntu3 Ubuntu:13.10/saucy [all])
Inst mate-mime-data (1.2.2-1+precise linuxmint:13/maya [all])
Inst mate-corba (1.2.2-3~precise linuxmint:13/maya [amd64])
Inst mate-conf-common (1.2.1-1~precise linuxmint:13/maya [all])
Inst mate-conf (1.2.1-1~precise linuxmint:13/maya [amd64])
Inst mate-vfs (1.2.1-2~precise linuxmint:13/maya [amd64])
Inst caja-common (1.2.1-1+precise linuxmint:13/maya [all])
Inst caja (1.2.1-1+precise linuxmint:13/maya [amd64])
Inst libcanberra-gtk-module (0.30-0ubuntu2 Ubuntu:13.10/saucy [amd64])
Inst libmarco (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst libmatecomponent (1.2.1-1~precise linuxmint:13/maya [amd64])
Inst libmate-common (1.2.0-2~precise linuxmint:13/maya [all])
Inst libmate (1.2.0-2~precise linuxmint:13/maya [amd64])
Inst libmatecanvas (1.2.0-2~precise linuxmint:13/maya [amd64])
Inst libmatecomponentui (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst libmatekbd (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst libmatekeyring (1.3.0-1 linuxmint:13/maya [amd64])
Inst libmatemenu (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst libmatenotify (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst libmatepanelapplet (1.2.1-3+precise linuxmint:13/maya [amd64])
Inst libmatepolkit (1.2.0-4+precise linuxmint:13/maya [amd64])
Inst libmateweather-common (1.2.0-2+precise linuxmint:13/maya [all])
Inst libmateweather (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst libsgutils2-2 (1.33-1build1 Ubuntu:13.10/saucy [amd64])
Inst libtasn1-3-bin (2.14-2 Ubuntu:13.10/saucy [amd64])
Inst mate-dialogs (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst marco-common (1.2.0-2+precise linuxmint:13/maya [all])
Inst marco (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst mate-desktop-common (1.2.0-3+precise linuxmint:13/maya [all])
Inst mate-desktop (1.2.0-3+precise linuxmint:13/maya [amd64])
Inst mate-icon-theme (1.2.0-2+precise linuxmint:13/maya [all])
Inst mate-keyring (1.3.0-1 linuxmint:13/maya [amd64])
Inst mate-menus (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst menu-xdg (0.5 Ubuntu:13.10/saucy [all])
Inst mate-polkit (1.2.0-4+precise linuxmint:13/maya [amd64])
Inst mate-panel-common (1.2.1-3+precise linuxmint:13/maya [all])
Inst mate-panel (1.2.1-3+precise linuxmint:13/maya [amd64])
Inst mate-power-manager-common (1.2.1-2+precise linuxmint:13/maya [all])
Inst mate-power-manager (1.2.1-2+precise linuxmint:13/maya [amd64])
Inst mate-settings-daemon-common (1.2.0-4+precise linuxmint:13/maya [all])
Inst mate-settings-daemon-gstreamer (1.2.0-4+precise linuxmint:13/maya [amd64])
Inst mate-settings-daemon (1.2.0-4+precise linuxmint:13/maya [all])
Inst mate-window-manager (1.2.0-2+precise linuxmint:13/maya [all])
Inst mate-session-manager (1.2.0-3+precise linuxmint:13/maya [amd64])
Inst mate-screensaver (1.2.0-2+precise linuxmint:13/maya [amd64])
Inst udisks (1.0.4-7build1 Ubuntu:13.10/saucy [amd64])
Conf libcanberra-gtk0 (0.30-0ubuntu2 Ubuntu:13.10/saucy [amd64])
Conf libdevmapper-event1.02.1 (2:1.02.74-6ubuntu4 Ubuntu:13.10/saucy [amd64])
Conf liblvm2app2.2 (2.02.95-6ubuntu4 Ubuntu:13.10/saucy [amd64])
Conf libmatecorba (1.2.2-3~precise linuxmint:13/maya [amd64])
Conf libmateconf (1.2.1-1~precise linuxmint:13/maya [amd64])
Conf libcaja-extension (1.2.1-1+precise linuxmint:13/maya [amd64])
Conf libmatedesktop (1.2.0-3+precise linuxmint:13/maya [amd64])
Conf libfam0 (2.7.0-17 Ubuntu:13.10/saucy [amd64])
Conf libmatevfs (1.2.1-2~precise linuxmint:13/maya [amd64])
Conf mate-vfs-common (1.2.1-2~precise linuxmint:13/maya [all])
Conf fuse-utils (2.9.0-1ubuntu3 Ubuntu:13.10/saucy [all])
Conf mate-mime-data (1.2.2-1+precise linuxmint:13/maya [all])
Conf mate-corba (1.2.2-3~precise linuxmint:13/maya [amd64])
Conf mate-conf-common (1.2.1-1~precise linuxmint:13/maya [all])
Conf mate-conf (1.2.1-1~precise linuxmint:13/maya [amd64])
Conf mate-vfs (1.2.1-2~precise linuxmint:13/maya [amd64])
Conf caja-common (1.2.1-1+precise linuxmint:13/maya [all])
Conf caja (1.2.1-1+precise linuxmint:13/maya [amd64])
Conf libcanberra-gtk-module (0.30-0ubuntu2 Ubuntu:13.10/saucy [amd64])
Conf libmarco (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf libmatecomponent (1.2.1-1~precise linuxmint:13/maya [amd64])
Conf libmate-common (1.2.0-2~precise linuxmint:13/maya [all])
Conf libmate (1.2.0-2~precise linuxmint:13/maya [amd64])
Conf libmatecanvas (1.2.0-2~precise linuxmint:13/maya [amd64])
Conf libmatecomponentui (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf libmatekbd (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf libmatekeyring (1.3.0-1 linuxmint:13/maya [amd64])
Conf libmatemenu (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf libmatenotify (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf libmatepanelapplet (1.2.1-3+precise linuxmint:13/maya [amd64])
Conf libmatepolkit (1.2.0-4+precise linuxmint:13/maya [amd64])
Conf libmateweather-common (1.2.0-2+precise linuxmint:13/maya [all])
Conf libmateweather (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf libsgutils2-2 (1.33-1build1 Ubuntu:13.10/saucy [amd64])
Conf libtasn1-3-bin (2.14-2 Ubuntu:13.10/saucy [amd64])
Conf mate-dialogs (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf marco-common (1.2.0-2+precise linuxmint:13/maya [all])
Conf marco (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf mate-desktop-common (1.2.0-3+precise linuxmint:13/maya [all])
Conf mate-desktop (1.2.0-3+precise linuxmint:13/maya [amd64])
Conf mate-icon-theme (1.2.0-2+precise linuxmint:13/maya [all])
Conf mate-keyring (1.3.0-1 linuxmint:13/maya [amd64])
Conf mate-menus (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf menu-xdg (0.5 Ubuntu:13.10/saucy [all])
Conf mate-polkit (1.2.0-4+precise linuxmint:13/maya [amd64])
Conf mate-panel-common (1.2.1-3+precise linuxmint:13/maya [all])
Conf mate-panel (1.2.1-3+precise linuxmint:13/maya [amd64])
Conf mate-power-manager-common (1.2.1-2+precise linuxmint:13/maya [all])
Conf mate-power-manager (1.2.1-2+precise linuxmint:13/maya [amd64])
Conf mate-settings-daemon-common (1.2.0-4+precise linuxmint:13/maya [all])
Conf mate-settings-daemon-gstreamer (1.2.0-4+precise linuxmint:13/maya [amd64])
Conf mate-settings-daemon (1.2.0-4+precise linuxmint:13/maya [all])
Conf mate-window-manager (1.2.0-2+precise linuxmint:13/maya [all])
Conf mate-session-manager (1.2.0-3+precise linuxmint:13/maya [amd64])
Conf mate-screensaver (1.2.0-2+precise linuxmint:13/maya [amd64])
Conf udisks (1.0.4-7build1 Ubuntu:13.10/saucy [amd64])
```

My advice is to look for another screen saver :) There's no saying what conflicts would arise if these packages were installed.

Kind regards

---

### Post by este.el.paz on 2013-05-03
> **matt_symes said:**
> Hi

I have been having a look at this. 
The "floating feet" screensaver is in the package mate-screensaver and that is in the repository..
This does not contain the "floating feet"" screensaver - and has not for a while. I could not see if in any of the xscreensaver packages.
You could add that repository to your sources, update and install it, however look what it will pull in - just for the "floating feet" screen saver.
This is the simulated run i did....
My advice is to look for another screen saver :) There's no saying what conflicts would arise if these packages were installed.

Kind regards

@Matt:

Thanks very kindly for that thorough answer, I try to accept the advice that's given whenever possible.  I did see that the Floating Feet were not part of the Xscreesaver package, but I was/am considering adding the whole MATE DE as another option from the XFCE, Xubuntu, LXDE . . . and then hopefully the Floating Feet would be part of that DE that would be logged into, and then of course all the packages for MATE would be installed . . . .  But, if that were do-able, which of the LM sources.list would I want in addition to what you've listed at the top of the page?  And, would you think that adding the whole MATE DE would cause conflicts in the system?  That might explain why there was the problem with the cursor in the LM system, where I had a number of DEs . . . MATE, XFCE, LXDE installed??  

So far that cursor issue has not occurred in the present Xubun 12.04 system with just LXDE added, and I don't want to mess it up, that's why I'm asking about  the wisdom or the way to do it right, but it seems like it should all "Be in the family" and try to "get along" with each other; whereas, perhaps just trying for the Floating feet screensaver alone might cause some problems while logged in to say, "Xubuntu" session . . . but if I was logged in "MATE" session it would just be part of that DE?  "MATE" doesn't show up in Xubuntu Synaptic search, so I'm assuming I would need to adjust my sources list to get it?  Would the 
```
deb http://packages.linuxmint.com/maya main upstream import
``` line you mentioned be enough to get Synaptic to find MATE?  Or should I just "let it go" until such time as Linux Mint would be the base system?  Certainly I could add that line and then see if synaptic would find "MATE DE" but, again, not knowing if that would cause internal conflict is the issue that I'm seeking the guidance on, etc.

Thanks again for your help,
e.e.p.

---

### Post by matt_symes on 2013-05-03
Hi

I think you would need to install the mate desktop/window manager to get mate-screensaver. You would not be able to use it in Xubuntu - i don't think.

To be honest, i have no idea if installing mate would create the problems you were having under Linux Mint. You would have to try it and see.

Anyway, to install Mate DE in Xubuntu, take a look at this

[http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html](http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html)

I have never used the Mate desktop so i may not be the best person to advise you. You may want to see if others will add something.

Kind regards

---

### Post by este.el.paz on 2013-05-04
> **matt_symes said:**
> Hi

I think you would need to install the mate desktop/window manager to get mate-screensaver. You would not be able to use it in Xubuntu - i don't think.
Anyway, to install Mate DE in Xubuntu, take a look at this

[http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html](http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html)

I have never used the Mate desktop so i may not be the best person to advise you. You may want to see if others will add something.

Kind regards

@matt_s:

Thanks again for the follow up and the link, that would solve the question of how to determine what gets added to the sources list, rather than adding it to the sources list and then trying to install MATE . . . .  Anyway, nothing ventured nothing gained; it looks like we might have a rare rainy day in LA tomorrow, so I might give it a try and see how it goes.  Just like I like GNOME, I also liked MATE, didn't have all the eye candy that Cinnamon has, but seemed to run cooler on the laptop . . . and, it has the Floating Feet screensaver which has to be one of the funniest screensavers . . . simple, white "feet" floating on black screen . . . beautiful in its own way.  : - )  Whoever designed it should get some kind of prize . . . well, I like it enough to add the MATE DE and see how it fairs working in the Xubuntu base environment . . . .

Thanks again for your help,

e.e.p.

---

