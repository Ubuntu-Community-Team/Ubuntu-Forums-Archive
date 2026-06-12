---
title: "[SOLVED] How can I tell which repo download is coming from?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-04-27
When downloading a program how can I tell which one of the repositories it is coming from?

---

### Post by Happy_Man on 2007-04-27
Well, if you go from a command line, when it downloads, it usually has the url of the repo the files are coming from displayed. From Synaptic, I don't think it does.

---

### Post by Najand on 2007-04-27
Before downloading, ```
 apt-cache show <PACKAGE> 
``` can show a complete information about the package <PACKAGE> and its repository.

---

### Post by wormser on 2007-04-27
I do install via apt-get.  I am getting a verification error and want to correct it by getting the key.   It does not list the repository in the details before the error.  That is why I am looking for which repository the files are coming from.

---

### Post by trak87 on 2007-04-27
At least in synaptic, if you right click on a package name and view the properties, it will describe which repository its coming from.

---

### Post by wormser on 2007-04-27
> **Najand said:**
> Before downloading, ```
 apt-cache show <PACKAGE> 
``` can show a complete information about the package <PACKAGE> and its repository.

The file looks like it is coming from universe.

>  apt-cache show libvlc0
Package: libvlc0
Priority: optional
Section: universe/libs
Installed-Size: 2064
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Sam Hocevar (Debian packages) <sam+deb@zoy.org>
Architecture: i386
Source: vlc
Version: 0.8.6.release-0ubuntu4
Replaces: vlc (<< 0.8.6-svn20060911.0.8.5-1-svn.debian-3)
Depends: libc6 (>= 2.5-0ubuntu1), libdbus-1-3 (>= 0.94), libdvbpsi4, libgcc1 (>= 1:4.1.2), libhal1 (>= 0.5), libogg0 (>= 1.1.3), libstdc++6 (>= 4.1.2), libtheora0
Conflicts: vlc (<< 0.8.6-svn20060911.0.8.5-1-svn.debian-3)
Filename: pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu4_i386.deb
Size: 984024
MD5sum: 2ffc3fb041cdff75cb73233b74b8f577
SHA1: c349d6906fc58919d5d080b160b0ec3bf31cf7bf
SHA256: 1fa48e1ee1cd092c71e48e35a37ff3eae16b25bb71272442320dc7e6b380e8ac
Description: multimedia player and streamer library
 This package contains the shared library required by applications using VLC
 features.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


>  sudo apt-key list
Password:
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/0C5A2783 2006-11-23
uid                  The Medibuntu Team <medibuntu@sos-sts.com>
sub   2048g/16C7105A 2006-11-23


I am getting a little lost here.  It appears to be coming from universe.  Shouldn't the universe key be set on default with ubuntu?

---

### Post by Najand on 2007-04-27
Run:```

$ sudo apt-get clean && sudo apt-get autoclean
$ sudo rm -rf /var/lib/apt/lists/partial/*
$ sudo apt-get update
$ sudo apt-get install libvlc0

```

---

### Post by wormser on 2007-04-27
> **Najand said:**
> Run:```

$ sudo apt-get clean && sudo apt-get autoclean
$ sudo rm -rf /var/lib/apt/lists/partial/*
$ sudo apt-get update
$ sudo apt-get install libvlc0

```

That did the trick.  Thank you.  I am not sure if I understand the commands.  It looks like the commands just cleaned and removed junk files in apt.  I do not understand why that would give me a key error.

Thanks again.

---

### Post by Najand on 2007-04-27
Your package was downloaded with faults. The first line just cleaned the partial parts of downloaded package. As a double standard the 2nd line removed the ones couldn't be removed by apt and i think you are familiar with 3rd adn 4th. Never forget to do update before installing new packages using apt or aptitute.

---

### Post by wormser on 2007-04-27
> **Najand said:**
> Your package was downloaded with faults. The first line just cleaned the partial parts of downloaded package. As a double standard the 2nd line removed the ones couldn't be removed by apt and i think you are familiar with 3rd adn 4th. Never forget to do update before installing new packages using apt or aptitute.

Thanks for the explanation and tip.

---

