---
title: "Synaptic trouble"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by JokkeW on 2008-04-05
Hi again!
I'm going to begin by excusing for this massive post, but here it goes:

I've recently written here about my ipv6 problem and that seems to be solved, but one problem is left. I can't really update my list and I can't install anything either.

I think there's something wrong with my /etc/apt/sources.list, when i try to "reload" the package list it says this:
```
http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-sv_SE.bz2: Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-sv_SE.bz2: Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz
```

I've tried to install the following;

Elisa
Opera
Amarok

Elisa and Opera are packagefiles that I've downloaded myself, but  it seems that it really doesn't care. When I mark the Elisa files for installation in Synaptic, it first comes up like this;
```
NOT AUTHENTICATED:
python-ylirc
gstreamer0.10-plugins-bad
gstreamer0.10-flv
To be installed:
gstreamer0.10-flv
gstreamer0.10-plugins-bad
python-pylirc
```

Then, at the next screen, it comes up like "Couldn't mark all for installation" and it looks like this;

```
elisa:
 depending on: elisa-core but it is not going to be installed
 depending on: elisa-plugins-good but it is not going to be installed
 depending on: elisa-plugins-bad but it is not going to be installed

elisa-core:
 depending on: python-pigment but it is not going to be installed
 depending on: python-pkg-resources  but it is not installable or
 	python-setuptools  but it is not installable
 depending on: python-twisted-core (>=2.2) but it is not installable
 depending on: python-twisted-web  but it is not installable

elisa-extra:
 depending on: elisa-core but it is not going to be installed
 depending on: elisa-plugins-good but it is not going to be installed
 depending on: elisa-plugins-bad but it is not going to be installed
 depending on: elisa-plugins-ugly but it is not going to be installed
 depending on: python-pkg-resources  but it is not installable or
 	python-setuptools  but it is not installable
 depending on: python-twisted-core (>=2.2) but it is not installable
 depending on: python-twisted-web  but it is not installable
 depending on: gstreamer0.10-ffmpeg  but it is not installable
 depending on: gstreamer0.10-plugins-ugly  but it is not installable
 depending on: gstreamer0.10-plugins-bad-multiverse  but it is not installable
 depending on: gstreamer0.10-fluendo-mpegdemux  but it is not installable
 depending on: gstreamer0.10-plugins-ugly-multiverse  but it is not installable

elisa-plugins-bad:
 depending on: elisa-plugins-good but it is not going to be installed
 depending on: python-avahi  but it is not installable
 depending on: python-daap  but it is not installable
 depending on: python-gpod  but it is not installable
 depending on: python-bluez  but it is not installable
 depending on: python-pigment but it is not going to be installed
 depending on: python-coherence but it is not going to be installed

elisa-plugins-good:
 depending on: python-pigment but it is not going to be installed
 depending on: python-pkg-resources  but it is not installable or
 	python-setuptools  but it is not installable
 depending on: python-twisted-core (>=2.2) but it is not installable
 depending on: python-twisted-web  but it is not installable
 depending on: python-avahi  but it is not installable

elisa-plugins-ugly:
 depending on: elisa-plugins-good but it is not going to be installed
 depending on: python-twill  but it is not installable
 depending on: python-beautifulsoup  but it is not installable
 depending on: python-gdata but it is not going to be installed
```

---

### Post by Michael.Godawski on 2008-04-05
Can you please post the output of your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by JokkeW on 2008-04-05
w@wimmerstedt-mediadator:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

EDIT: Sorry for not laying it in code.

---

### Post by Michael.Godawski on 2008-04-05
Well all your sources except one are commented out with the # sign. 

So go to 
System > Administration > Software Sources

and enable all sources (check the box) except source code and CD.

Then "Reload" or in terminal
```
sudo apt-get update 
```

Now try again to install the application you want to install.

---

### Post by JokkeW on 2008-04-05
When i try to reload, i get this messege: "Could not download all repository indexes".

---

### Post by Michael.Godawski on 2008-04-05
And what error do you get when you run ```
 sudo apt-get update
```.
Perhaps that error messages will be somewhat more meaningful that the last one.

---

### Post by JokkeW on 2008-04-05
```
Wrong http://elisa.fluendo.com gutsy Release.gpg
  Could not connect to elisa.fluendo.com:80 (1.0.0.0). - connect (113 No route to host)
Wrong http://archive.ubuntu.com gutsy Release.gpg                                            
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Wrong http://elisa.fluendo.com gutsy/main Translation-sv_SE                                  
  Could not connect to elisa.fluendo.com:80 (1.0.0.0). - connect (113 No route to host)

```

If you're wondering about elisa, it's there because i tried to follow a guide on how to install it.

---

### Post by Michael.Godawski on 2008-04-05
OK elisa makes trouble. Can you just test if you can install something different via the add/remove application?

---

### Post by JokkeW on 2008-04-05
I tried to install Abuse, a game that i've actually had on the computer when i've tried ubuntu earlier last year. It failed.

```
Abuse cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```

---

