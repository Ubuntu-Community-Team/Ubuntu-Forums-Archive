---
title: "[SOLVED] deb pkg managment error :'("
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-02-17
howdy folks, fresh install of ubuntu 7.10 (again) and i get this error... btw, my internet was a little iffy and stuff...

```
E: ttf-opensymbol: subprocess post-installation script returned error exit status 42
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured


```

how do I fix this? thanks, my sourcelist is default

sv

---

### Post by PmDematagoda on 2008-02-17
Post the output of:-
```
sudo dpkg --configure -a
```
and
```
sudo apt-get install -f
```

---

### Post by staticvoid on 2008-02-17
this is a ton of output...

**sudo dpkg --configure -a**
> Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts: failed to write cache
/usr/share/fonts/X11: failed to write cache
/usr/share/fonts/X11/100dpi: failed to write cache
/usr/share/fonts/X11/75dpi: failed to write cache
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/fonts/X11/encodings: failed to write cache
/usr/share/fonts/X11/encodings/large: failed to write cache
/usr/share/fonts/X11/misc: failed to write cache
/usr/share/fonts/X11/util: failed to write cache
/usr/share/fonts/truetype/arphic: failed to write cache
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-dejavu: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/local/share/fonts: failed to write cache
/var/lib/defoma/fontconfig.d/B: failed to write cache
/var/lib/defoma/fontconfig.d/D: failed to write cache
/var/lib/defoma/fontconfig.d/E: failed to write cache
/var/lib/defoma/fontconfig.d/F: failed to write cache
/var/lib/defoma/fontconfig.d/H: failed to write cache
/var/lib/defoma/fontconfig.d/J: failed to write cache
/var/lib/defoma/fontconfig.d/K: failed to write cache
/var/lib/defoma/fontconfig.d/L: failed to write cache
/var/lib/defoma/fontconfig.d/M: failed to write cache
/var/lib/defoma/fontconfig.d/N: failed to write cache
/var/lib/defoma/fontconfig.d/O: failed to write cache
/var/lib/defoma/fontconfig.d/P: failed to write cache
/var/lib/defoma/fontconfig.d/R: failed to write cache
/var/lib/defoma/fontconfig.d/S: failed to write cache
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 42
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
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


**sudo apt-get install -f**
this gave:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.

..plus  what is above and the last part was different:
> dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
**E: Sub-process /usr/bin/dpkg returned an error code (1)**


there you have it :) thanks a bunch. i hope this is easy to fix with removing the packages or reinstalling them and stuff..  :)

sv

---

### Post by staticvoid on 2008-02-17
btw, sweet avatar ;)

---

### Post by PmDematagoda on 2008-02-17
That looks like a problem I have never seen before.

I do not have much of a solution except a suggestion that you reinstall OpenOffice and all related packages. Also, if you are going to do that just clean the archives folder using:-
```
sudo apt-get clean
```
and then reinstall OpenOffice.

You may wait for someone else to post a better solution or suggestion.

> btw, sweet avatar 
Thank you:), it was just an avatar I conjured up using some of the logos of the major free distros.

---

### Post by staticvoid on 2008-02-17
how do i reinstall openoffice? just set everything in synaptic that has "openoffice" in the name to reinstall?

i tried clean but it still would'nt work... and i'm stil getting those font errors.. maybe also reinstal mttfonts?

sv

EDIT: nevermind, i reinstalled

---

### Post by staticvoid on 2008-02-17
argh.. after reintsalling:
> E: ttf-opensymbol: subprocess post-installation script returned error exit status 42
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-style-tango: dependency problems - leaving unconfigured
E: openoffice.org-help-en-us: dependency problems - leaving unconfigured


hmm!!  : / maybe i have dependancy problems?  :)

:(

sv

---

### Post by staticvoid on 2008-02-17
btw openoffice still works... its just a bunch of errors though... why? stuff even installs, just it gives errors...  hmm  : / i have never encountered this...

sv

---

### Post by PmDematagoda on 2008-02-17
> i tried clean but it still would'nt work... and i'm stil getting those font errors.. maybe also reinstal mttfonts?
The command just removes the downloaded packages from the archives folder, you may also reinstall mttfonts as well.

> how do i reinstall openoffice? just set everything in synaptic that has "openoffice" in the name to reinstall?
Yes, that should do it.

---

### Post by staticvoid on 2008-02-17
looks like its screwing up right after install here:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-19.png[/IMG]

: /  thunar still was installed btw

sv

---

### Post by staticvoid on 2008-02-17
hmm, i downloaded a deb and tried to install and it wouldn't... now this is getting annoying : /

---

### Post by staticvoid on 2008-02-17
bump...


i don't want to reinstall  :(

---

### Post by staticvoid on 2008-02-17
could it be openoffice 4 beta thats screwing things up...?

sv

---

### Post by K.Mandla on 2008-02-19
I'm seeing this too, on three different machines now. It's definitely somehow linked to the ttf-opensymbol package. Now looking for bug report. ...

Edit: [This]("https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/144771") suggests it might be tied to a locale issue, or at least fixable by installing *locales*. I won't get a chance to check until later tonight.

Edit: Actually, I think it's more a bug along these lines: [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/104553](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/104553) 

There are a number of possible fixes on that page. I'll try some tonight.

---

### Post by staticvoid on 2008-02-19
oh man... guess what? I saolved it! but then i switched to ArchLinux... and know after configuring so many files and setting up openbox and everything... i forget what i did! argh... i'm so sorry to all those who are having this problem...

basically i removed everything cleaned purged ran the sudo dpkg-fix option thing (what is that?? perty sure that did it) now i'm using pacman anyway...

i think its (after checking here: [http://diablo.ucsc.edu/~wgscott/debian/apt-dpkg-ref.html](http://diablo.ucsc.edu/~wgscott/debian/apt-dpkg-ref.html))
> sudo apt-get dpkg --configure --pending

or...

sudo apt-get --dpkg-reconfigure

hope that helps : / again, sorry... i should have posted the fix right after i solved the problem to benefit everybody... but i was imigratin' ;)

sv

---

