---
title: "[SOLVED] Broken Package open office"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-10-05
Help please this is my error

E: /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/share/template/wizard/letter/pl/bus-office_l.ott')

any ideas?

---

### Post by nowshining on 2007-10-05
applications - terminal

and paste the output of 

sudo apt-get install -f

enter your password, don't worry nothing will show as you type as this is normal and just type out YOUR password as usual and then hit enter. :)

---

### Post by J11Gyro on 2007-10-05
Did that and got same error so totally uninstalled open office   now trying to get it re-installed

---

### Post by nowshining on 2007-10-05
hmmm u went without me seeing what it said, as it could of very well of ruint ur whole system - I had it happen myself before. :) now you gotta do a whole re-install - of it, do this go into system - administration - synaptic package manager and do a search for openoffice right click and click install if it's now uninstalled when done at the top click apply it will / should download it from the internet along with all the needed libs, etc..

---

### Post by J11Gyro on 2007-10-05
Tried the reinstall and end up with the exact same error message. Seems a few people are having prob's with openoffice right now. Seems all updates are running way slow right now or not even finishing. Sorry I did it so fast but back would not let me sleep so had nothing better to do LOL

---

### Post by philinux on 2007-10-05
Me too. Wish I'd seen this thread before letting update do its thing. What's the cure.

{update] synaptic shows no broken packages and open office still works.

---

### Post by por100pre1 on 2007-10-05
Weird. Try this:

```
sudo dpkg --configure -a
```

---

### Post by philinux on 2007-10-05
Is this world wide or what? Something very odd with this office update. :confused:

philcb@philcb-desktop:~$ sudo dpkg --configure -a
Password:
Setting up ttf-opensymbol (2.2.0-1ubuntu5) ...
Updating fontconfig cache...
/usr/share/fonts/truetype: failed to write cache
/usr/share/fonts/truetype/msttcorefonts: failed to write cache
/var/lib/defoma/fontconfig.d: failed to write cache
/var/lib/defoma/fontconfig.d/A: failed to write cache
/var/lib/defoma/fontconfig.d/C: failed to write cache
/var/lib/defoma/fontconfig.d/G: failed to write cache
/var/lib/defoma/fontconfig.d/I: failed to write cache
/var/lib/defoma/fontconfig.d/T: failed to write cache
/var/lib/defoma/fontconfig.d/V: failed to write cache
/var/lib/defoma/fontconfig.d/W: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
 openoffice.org-filter-mobiledev
philcb@philcb-desktop:~$

---

### Post by Johnny3 on 2007-10-05
Try System/Administration/Synaptic Package Manager/Edit/fix Broke packages
Thanks Johnny3
Gainesville Fl

---

### Post by philinux on 2007-10-05
Tried fix broken packages even though it didn't show any under broken. It gave a message dependencies successfully fixed so tried 

philcb@philcb-desktop:~$ sudo dpkg --configure -a    again and got all the same errors as posted before. :confused:

[edit] just looked in synaptic ad it shows the install ok - whats going on with these errors?

---

### Post by Johnny3 on 2007-10-05
Did you try mark for complete removal. Then turn pc off and back on do update then in Synaptic do a reload? 
Thanks Johnny3
Gainesville Fl

---

### Post by philinux on 2007-10-05
Surely auto updates are checked for bugs - what I'd like to know is where the errors are coming from and why?

---

### Post by philinux on 2007-10-05
From the errors it seems to be relating to ttf-opensymbol  updating fontconfig.

Tried reinstall ttf-opensymbol no change same errors.

Please dont post to this thread I started a new one with title

Todays auto update broke open office dependencies

We might get the admins attention - he hopes !

---

### Post by J11Gyro on 2007-10-06
Have used all commands in sudo as recommended and even tried a fresh install from CD and no luck. Now I am considering reload of feisty or waiting for gutsy to be released. I don't have open office on my system anymore though :(

---

### Post by philinux on 2007-10-06
See my solved thread. Its a known bug too

---

### Post by philinux on 2007-10-06
Attached sources - good luck

---

### Post by nowshining on 2007-10-07
mine is fine in Gutsy ;)

---

### Post by nowshining on 2007-10-07
oh and ur sources to me looks fine. :)

---

### Post by Arcturus691 on 2007-10-19
I think the problem is that the tar file:  openoffice.org-common_2.2.0-1ubuntu5_all.deb
is corrupt. I just downloaded it from    [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.2.0-1ubuntu5_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.2.0-1ubuntu5_all.deb)
and copied to the /var/cache/apt/archive directory and removed the lock file from the same dir and then ran the command:
 sudo apt-get install -f

and get the following error:
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive

Who should I email at ubuntu so they can reload the file?

I forgot to mention this is for Feisty 7.04, the link above is from that section.

---

### Post by Arcturus691 on 2007-10-19
Synaptic gives this error:
E: /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2

---

