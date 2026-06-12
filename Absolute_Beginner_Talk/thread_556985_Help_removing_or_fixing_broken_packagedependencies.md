---
title: "Help removing or fixing broken package/dependencies"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by killaray on 2007-09-22
truthfully i dont know how this all started.. all i can say was that i was installing some python packages for exaile and i hit install in synaptic and it ran for a quick second then cut off.. then i checked again and the packages hadnt installed, so i hit apply one more time and same thing happened. i close synaptic and try an apt-get upgrade threw terminal and it says ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-apm but it is not installed
E: Unmet dependencies. Try using -f.

```

so then i open synaptic and it says theres a broken dependency or somethin... so anyway ive been tryin to reinstall this crappy  xserver-xorg-video-all with aptitude so that it would install all its dependencies along with it and its a no go with this error ```
Building tag database... Done      
The following packages are BROKEN:
  xserver-xorg-video-all 
The following packages have been kept back:
  git-core 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-apm but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
xserver-xorg-video-apm [1:1.1.1-3ubuntu1 (feisty)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  xserver-xorg-video-apm 
The following packages have been kept back:
  git-core 
The following NEW packages will be installed:
  xserver-xorg-video-apm 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/65.0kB of archives. After unpacking 209kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version

```

so now im stuck, ive tried sudo aptitude -f install and everything to no avail.. is there someway to fix this?

---

### Post by alienexplorers on 2007-09-22
Try:

> sudo aptitude update
sudo aptitude upgrade

Try running:

> sudo aptitude install xserver-xorg-video-apm

If that does not work try:

> dpkg --configure -a

---

### Post by JNowka on 2007-09-22
Have you tried to download the package off the net and install it with dpkg ?   

If not go [here]("http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-apm") and download the file for your computer.

Then open up a terminal and cd to where the file is.  Finally type in, dpkg -i PackageName.deb, where PackageName is the name of your package you downloaded.

Let me know if this works.

---

### Post by killaray on 2007-09-22
ive tried those already.. come out with similar errors as posted in OP

---

### Post by JNowka on 2007-09-22
Ok try "sudo aptitude reinstall xserver-xorg-video-all"

---

### Post by killaray on 2007-09-22
```
killaray@Killa-PC:~$ sudo aptitude reinstall xserver-xorg-video-all
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  xserver-xorg-video-all 
The following packages have been kept back:
  git-core 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/25.8kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-apm but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
xserver-xorg-video-apm [1:1.1.1-3ubuntu1 (feisty)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  xserver-xorg-video-apm 
The following packages have been kept back:
  git-core 
The following packages will be REINSTALLED:
  xserver-xorg-video-all 
The following NEW packages will be installed:
  xserver-xorg-video-apm 
0 packages upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/90.9kB of archives. After unpacking 209kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version
killaray@Killa-PC:~$ sudo aptitude reinstall xserver-xorg-video-apm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
xserver-xorg-video-apm is not currently installed, so it will not be reinstalled.
The following packages are BROKEN:
  xserver-xorg-video-all 
The following packages have been kept back:
  git-core 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-apm but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
xserver-xorg-video-apm [1:1.1.1-3ubuntu1 (feisty)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  xserver-xorg-video-apm 
The following packages have been kept back:
  git-core 
The following NEW packages will be installed:
  xserver-xorg-video-apm 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/65.0kB of archives. After unpacking 209kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version
```

---

### Post by killaray on 2007-09-23
anyone?

---

### Post by alienexplorers on 2007-09-23
Try with a > sudo dpkg --clear-avail && sudo apt-get update

---

### Post by killaray on 2007-09-23
well that cleared the update status but i still cant download the dependencies i know to fix the broken package

---

### Post by killaray on 2007-09-24
anyone have anyother ideas?

---

### Post by RomeReactor on 2007-09-24
Hi. Have you tried **sudo apt-get install -f**?

---

### Post by killaray on 2007-09-24
yes.. its the first thing i tried since thats wut terminal says to do

heres the error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libzvbi-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xserver-xorg-video-apm
The following NEW packages will be installed:
  xserver-xorg-video-apm
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/65.0kB of archives.
After unpacking 209kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by RomeReactor on 2007-09-25
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libzvbi-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xserver-xorg-video-apm
The following NEW packages will be installed:
  xserver-xorg-video-apm
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/65.0kB of archives.
After unpacking 209kB of additional disk space will be used.
Do you want to continue [Y/n]? 
[B]dpkg: parse error, in file `/var/lib/dpkg/status' near line 4024 package `xserver-xorg-video-apm':
 missing version[/B]
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Try this: open the file with gedit:
```
gksudo gedit /var/lib/dpkg/status
```
 Now press the "Find" button and paste:
```
Package: xserver-xorg-video-apm
```
and see which version it shows; I think it should read:
```
Package: xserver-xorg-video-apm
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 208
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
**Version: 1:1.1.1-3ubuntu1**
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-apm
Provides: xserver-xorg-video-1.0
Depends: libc6 (>= 2.5-0ubuntu1), xserver-xorg-core (>= 2:1.1.1-1)
Conflicts: xserver-xorg-driver-apm
Description: X.Org X server -- APM display driver
 This package provides the driver for the Alliance Pro Motion family
 of video cards; specifically, the 6420, 6422, AT24, AT25, and AT3D
 cards.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'driver/xf86-video-apm' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
```

I can't assure you that fixing that line will solve the problem; and I also seem to remember you could delete the file and do a **sudo apt-get update** and it would regenerate. **But**: I suggest you don't do it unless someone else confirms this.

---

### Post by killaray on 2007-09-25
this is what i got


```
Package: xserver-xorg-video-apm
Status: install ok installed
Priority: optional
Section: x11
```

---

### Post by RomeReactor on 2007-09-25
That's all? do other packages show up after that, or does the file end there?

---

### Post by killaray on 2007-09-25
holy lord.. welll i deleted that entry and did **sudo apt-get install -f** again... and it worked.. thanks alot Rome Reactor

---

### Post by killaray on 2007-09-25
> **RomeReactor said:**
> That's all? do other packages show up after that, or does the file end there?

there were more after that but i gotta working.. thanx

---

