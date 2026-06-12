---
title: "Update and Upgrade problems - packages not downloading"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Nickb-k on 2006-05-29
Hi,

I'm trying the uprage from Hoary Hedgehog (5.04) to Breezy.  My main reasons for upgrading are that I have some problems with my wireless network card and because recently I have been having problems with apt-get.  When I try to intall a program using apt-get install I get:

```
nick@nick:~$ sudo apt-get install gpsbabel
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gpsbabel: Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu15 is to be installed
            Depends: libusb-0.1-4 (>= 2:0.1.10a) but 1:0.1.8-17ubuntu2 is to be installed
E: Broken packages

```

So I've tried the following to upgrade:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Update runs fine, but upgrade returns this message:

```

nick@nick:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  855resolution classpath d4x endeavour2 gaim-guifications gnome-gv gnustep-back
  gnustep-base-common gnustep-gui-common gnustep-make gpsdrive gstreamer0.8-a52dec
  gstreamer0.8-mad gtkhtml3.6 gworkspace.app irb1.8 lesstif2 libffcall1 libgal2.4-0
  libgal2.4-common libgnustep-base1.10 libgnustep-gui0.9 libgtk2-gladexml-perl
  libgtkhtml3.6-18 libneon23 libreadline-ruby1.8 linux-restricted-modules-386 rdoc1.8
  totem-xine xmms-mad
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.

```

The contents of /etc/apt/sources.list are:

```

## Uncomment the following two lines to fetch updated software from the network
 deb http://gb.archive.ubuntu.com/ubuntu hoary main restricted
 deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gb.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

 deb http://archive.ubuntu.com/ubuntu/ breezy universe restricted multiverse

```

I guess that I have to update the contents of the file above, but I don't know what to insert.

Thanks in advance for the help!

---

### Post by zhoux on 2006-05-29
i think if you want to update to the next version, you can either do:
1. sudo apt-get dist-upgrade -d
or
2. change all "hoary" in sources.list to "breezy" or "dapper"

EDIT: I concur w/ cmarker

---

### Post by cmarker on 2006-05-29
If you wait a few days it would be best to upgrade to dapper when it is released on Thursday June 1st.

---

### Post by macdo on 2006-05-30
From the wiki: 
[quote=Ubuntu Wiki]Upgrading from Ubuntu releases prior to 5.10

   1.      Upgrade to Ubuntu 5.10 (see [BreezyUpgradeNotes]("https://wiki.ubuntu.com/BreezyUpgradeNotes"))
   2.      Follow the [above instructions]("https://wiki.ubuntu.com/BreezyUpgradeNotes") for upgrading from 5.10[/quote]

---

