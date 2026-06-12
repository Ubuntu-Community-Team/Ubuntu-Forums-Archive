---
title: "Azereus and Mplayer"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by taterknight on 2005-10-22
Hi, I just installed ubuntu on this computer two days ago and am having trouble playing videos (WMV format and DVDs) and wish to be able to use azureus.  Can anyone tell me exactly what I need to do, what to download, what to enter into the terminal, etc. Thank You

---

### Post by manicka on 2005-10-22
For Azureus

[http://www.ubuntuforums.org/showthread.php?t=74881&highlight=how-to+azureus](http://www.ubuntuforums.org/showthread.php?t=74881&highlight=how-to+azureus)

WMV and DVD

add the following to your sources.list by

```
sudo gedit /etc/apt/sources.list
```

add the following to the sources.list
```
## mirror provided thanks to OVH http://ovh.com
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
```

save and quit, then in a terminal

```
sudo apt-get update
sudo apt-get install w32codecs libdvdcss2
```

---

### Post by taterknight on 2005-10-22
Heres what I did in order to get the videos to work.
taters@Joey:~$ sudo gedit /etc/apt/sources.list
Password:
taters@Joey:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [19.6kB]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:6 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages [546B]
Get:7 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages [1119B]
Get:8 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources [316B]
Get:9 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources [288B]
Fetched 41.9kB in 3s (13.8kB/s)
Reading package lists... Done
taters@Joey:~$ sudo apt-get install w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  azureus: Depends: libcommons-cli-java but it is not going to be installed
           Depends: liblog4j1.2-java but it is not going to be installed
           Depends: libseda-java but it is not going to be installed
           Depends: libswt-gtk-3.1-java but it is not going to be installed
           Depends: sun-j2re1.5 but it is not going to be installed or
                    java2-runtime
  w32codecs: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by taterknight on 2005-10-22
Also heres my azureus info.
taters@Joey:~$ sudo apt-get install j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java
Password:
Reading package lists... Done
Building dependency tree... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate
taters@Joey:~$ wget -c  [http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.4-3_all.deb](http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.4-3_all.deb)
--17:54:20--  [http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.4-3_all.deb](http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.4-3_all.deb)
           => `azureus_2.3.0.4-3_all.deb'
Resolving ftp.us.debian.org... 128.101.80.133, 216.37.55.114, 204.152.191.7, ...Connecting to ftp.us.debian.org|128.101.80.133|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,771,474 (4.5M) [application/x-debian-package]

100%[====================================>] 4,771,474      1.55M/s

17:54:23 (1.55 MB/s) - `azureus_2.3.0.4-3_all.deb' saved [4771474/4771474]

taters@Joey:~$ sudo dpkg -i azureus_2.3.0.4-3_all.deb
Selecting previously deselected package azureus.
(Reading database ... 63150 files and directories currently installed.)
Unpacking azureus (from azureus_2.3.0.4-3_all.deb) ...
dpkg: dependency problems prevent configuration of azureus:
 azureus depends on libcommons-cli-java; however:
  Package libcommons-cli-java is not installed.
 azureus depends on liblog4j1.2-java; however:
  Package liblog4j1.2-java is not installed.
 azureus depends on libseda-java; however:
  Package libseda-java is not installed.
 azureus depends on libswt-gtk-3.1-java; however:
  Package libswt-gtk-3.1-java is not installed.
 azureus depends on sun-j2re1.5 | java2-runtime; however:
  Package sun-j2re1.5 is not installed.
  Package java2-runtime is not installed.
dpkg: error processing azureus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 azureus

---

### Post by taterknight on 2005-10-22
I wasn't sure about how to do the azureus properly, because i didnt understnad that help post, thank you for all help in advance.

---

### Post by manicka on 2005-10-22
Ok, you need to enable the multiverse and universe repos as well

add them with the method at this link then try the above again

[http://doc.ubuntu.com/gnome/faqi386/C/ch02.html#addinguniverse](http://doc.ubuntu.com/gnome/faqi386/C/ch02.html#addinguniverse)

---

### Post by taterknight on 2005-10-22
Ok, after I download and everything, what do I need to do in order to watch the DVDs, WMVs, etc.

---

### Post by manicka on 2005-10-22
to watch dvd's, wmv's etc, install totem-xine or mplayer

mplayer is also a better plugin for mozilla/firefox than the default totem

how-to here
[http://www.ubuntuforums.org/showthread.php?t=76946](http://www.ubuntuforums.org/showthread.php?t=76946)

---

