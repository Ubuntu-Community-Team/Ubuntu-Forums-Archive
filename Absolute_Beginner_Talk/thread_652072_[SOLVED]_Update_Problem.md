---
title: "[SOLVED] Update Problem"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by jfd on 2007-12-28
When I hover over the orange update star i get this message:

*This usually means that your installed packages have unmet dependencies*

When I try to update I get this:

[I]Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/I]

So I do that, and I get this:

[I]The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2 libwxgtk2.6-0 libqt4-core libdv-bin libxosd2 libqt4-gui
  libsynfig0 libxml++2.6c2a libwxbase2.6-0 lsdvd libswscale1d ffmpeg
  libgtk1.2-common libtar libimlib2 libsdl-image1.2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdelibs-data
The following NEW packages will be installed
  kdelibs-data
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
8 not fully installed or removed.
Need to get 0B/7295kB of archives.
After unpacking 28.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 101415 files and directories currently installed.)
Unpacking kdelibs-data (from .../kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

I tried the apt-get auto remove and I got this:

*E: Unmet dependencies. Try using -f.*

Can anybody help me fix this? Any help would be greatly appreciated.

---

### Post by overdrank on 2007-12-28
HI and you can try the commands
```
sudo apt-get autoremove
sudo apt-get autoclean
```
Or you can replace apt-get with aptitude if you prefer.

---

### Post by jfd on 2007-12-28
I tried all 4 commands and I still get the same message when I try to update :( 

Any ideas?

---

### Post by philinux on 2007-12-28
It looks like its telling you to do

sudo apt-get auto remove -f

---

### Post by jfd on 2007-12-28
I tried that and I got:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2 libwxgtk2.6-0 libqt4-core libdv-bin libxosd2 libqt4-gui
  libsynfig0 libxml++2.6c2a libwxbase2.6-0 lsdvd libswscale1d ffmpeg
  libgtk1.2-common libtar libimlib2 libsdl-image1.2
The following extra packages will be installed:
  kdelibs-data
The following packages will be REMOVED
  ffmpeg libdv-bin libglib1.2 libgtk1.2 libgtk1.2-common libimlib2 libqt4-core
  libqt4-gui libsdl-image1.2 libswscale1d libsynfig0 libtar libwxbase2.6-0
  libwxgtk2.6-0 libxml++2.6c2a libxosd2 lsdvd
The following NEW packages will be installed
  kdelibs-data
0 upgraded, 1 newly installed, 17 to remove and 8 not upgraded.
8 not fully installed or removed.
Need to get 0B/7295kB of archives.
After unpacking 8585kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 101415 files and directories currently installed.)
Unpacking kdelibs-data (from .../kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
[B]Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code[/B] (1)
[/I]

So i guess it's the bit in bold that needs fixing, but how do I fix it?

---

### Post by philinux on 2007-12-28
sudo apt-get -f  install

Try that.

---

### Post by jfd on 2007-12-28
I get:

[I]Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code[/I]

:(

---

### Post by philinux on 2007-12-28
This might help 

sudo dpkg --configure -a

---

### Post by jfd on 2007-12-28
OK I've got somewhere, it seems to be a problem with a package I tried to install a while ago called Kaffieine. It didn't install properly, so I guess that is what is creating the problem. I can still run the programe but I get loads of errors, so I need to remove it but I don't know how. Here is what I got when I tried your sudo dpkg -configure -a:
[I]
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on kdelibs-data (>> 4:3.5.8); however:
  Package kdelibs-data is not installed.
 kdelibs4c2a depends on kdelibs-data (<< 4:3.5.9); however:
  Package kdelibs-data is not installed.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kaffeine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine-xine:
 kaffeine-xine depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 kaffeine-xine depends on kaffeine; however:
  Package kaffeine is not configured yet.
dpkg: error processing kaffeine-xine (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdelibs4c2a
 kaffeine
 kaffeine-xine[/I]

---

### Post by jfd on 2007-12-29
Can anybody help?

---

### Post by PmDematagoda on 2007-12-29
Post the output of:-

```
cat /etc/apt/sources.list
```

---

### Post by overdrank on 2007-12-29
> **jfd said:**
> Can anybody help?

Hi and this may help 
[http://ubuntuforums.org/showthread.php?t=599049](http://ubuntuforums.org/showthread.php?t=599049)
The post made by Jaco Du Toit. It appears to be the same type of error you are receiving. Good luck!

---

### Post by jfd on 2007-12-29
I tried some of the stuff from the link and it started to update through the terminal but then i just got:

[I]Unpacking replacement findutils ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/I]

As for the output of cat etc/apt/sources.list i got:

[I]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
[/I]

---

### Post by overdrank on 2007-12-29
HI and when you say you tried some of the stuff, the one I had suggested would be 
```
cd /var/cache/apt/archives
```
And then once in that directory use 
```
sudo rm kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb
``` Or what ever that deb is giving the error. That is what worked for that user.

---

### Post by jfd on 2007-12-31
I still get the same message come up :( :confused:

---

### Post by jfd on 2008-01-01
Fixed it, I just ran:

*sudo aptitude purge kaffeine*

Kaffeine is what the broken packages where.

---

