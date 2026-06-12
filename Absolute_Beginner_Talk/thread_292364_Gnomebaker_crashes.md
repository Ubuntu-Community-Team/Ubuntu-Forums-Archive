---
title: "Gnomebaker crashes"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by requiem_gr on 2006-11-03
I need to write a bin file, so I started looking for a cd-burning program. After a little search on the forums I found about k3b. Tried to install it, but I couldn't do it (maybe 'cause I use Gnome, or something... I'm a complete newbie.. :) ). At last I installed Gnomebaker. But it simply crashes right after I execute it. With no prior warning. I've unistalled and installed several times. Also tried to execute it with the sudo command. The same thing.

I'm posting a new thread since I couldn't find anyone having similar problems with mine.

---

### Post by Bachstelze on 2006-11-03
sudo apt-get install k3b, what's the problem ?

---

### Post by bulldog on 2006-11-03
Try k3b again.
```
sudo aptitude install k3b
```

---

### Post by requiem_gr on 2006-11-03
> **HymnToLife said:**
> sudo apt-get install k3b, what's the problem ?

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
  k3b: Depends: k3blibs (>= 0.11.23) but it is not going to be installed
       Depends: kdelibs4 (>= 4:3.4.0) but it is not going to be installed
       Depends: libarts1 (>= 1.3.2) but it is not going to be installed
       Depends: libqt3c102-mt (>= 3:3.3.3) but it is not going to be installed
       Depends: kdebase-bin but it is not going to be installed
       Depends: kcontrol but it is not going to be installed
E: Broken packages

----

Same deal with : sudo aptitude install k3b

---

### Post by requiem_gr on 2006-11-03
I have to correct my previous post, as when I give : sudo aptitude install k3b, I get :

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  amarok kdelibs-bin kdelibs-data kdelibs4 kdelibs4c2a kfilereplace
  klinkstatus kommander kpdf ktorrent ktouch libarts1c2a libavahi-qt3-1
  libcupsys2 libkdeedu3 libopenexr2c2a quanta
The following NEW packages will be automatically installed:
  akode k3blibs kcontrol kdebase-bin kdebase-data libarts1 libcdio0
  libcupsys2-gnutls10 libflac++4 libflac6 libgnutls11 libiso9660-0 libltdl3
  liboggflac1 libopenexr2 libqt3c102-mt libsamplerate0 libssl0.9.7
  libvcdinfo0 vcdimager
The following packages will be automatically REMOVED:
  libqt3-mt
The following NEW packages will be installed:
  akode k3b k3blibs kcontrol kdebase-bin kdebase-data libarts1 libcdio0
  libcupsys2-gnutls10 libflac++4 libflac6 libgnutls11 libiso9660-0 libltdl3
  liboggflac1 libopenexr2 libqt3c102-mt libsamplerate0 libssl0.9.7
  libvcdinfo0 vcdimager
The following packages will be REMOVED:
  libqt3-mt
0 packages upgraded, 22 newly installed, 1 to remove and 0 not upgraded.
Need to get 32.6MB/33.3MB of archives. After unpacking 82.4MB will be used.
The following packages have unmet dependencies:
  kpdf: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  libavahi-qt3-1: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  libarts1c2a: Depends: libqt3-mt (>= 3:3.3.5) but it is not installable
               Conflicts: libarts1 but 1.4.0-0pre1ubuntu3 is to be installed.
  kdelibs4c2a: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
               Conflicts: kdelibs4 but 4:3.4.0-0ubuntu3.6 is to be installed.
  kdelibs4: Depends: kdelibs-bin (= 4:3.4.0-0ubuntu3.6) but 4:3.5.2-0ubuntu18.1 is installed.
  kfilereplace: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  klinkstatus: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  ktouch: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  libopenexr2c2a: Conflicts: libopenexr2 but 1.2.1-2 is to be installed.
  amarok: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  kommander: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  kdelibs-bin: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  quanta: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  ktorrent: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  libkdeedu3: Depends: libqt3-mt (>= 3:3.3.6) but it is not installable
  kdelibs-data: Conflicts: kdelibs4 but 4:3.4.0-0ubuntu3.6 is to be installed.
  libcupsys2: Conflicts: libcupsys2-gnutls10 (<= 1.1.23-11) but 1.1.23-1ubuntu12 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
akode [Not Installed]
k3b [Not Installed]
k3blibs [Not Installed]
kcontrol [Not Installed]
kdebase-bin [Not Installed]
kdelibs4 [Not Installed]
libarts1 [Not Installed]
libcupsys2-gnutls10 [Not Installed]
libopenexr2 [Not Installed]
libqt3-mt [3:3.3.6-1ubuntu6.1 (now)]
libqt3c102-mt [Not Installed]

Score is 91

---

### Post by Bachstelze on 2006-11-03
Hmm, please paste your sources.list...

---

### Post by requiem_gr on 2006-11-03
I'm feeling pretty stupid asking this, but how do you open sources.list?

I hope you'll excuse a complete newbie.. :-?

---

### Post by requiem_gr on 2006-11-03
Took me a while but I found it.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by requiem_gr on 2006-11-04
Sorry for being hasty on this, but I really need to backup my bin file. Can anyone give me some help?

---

### Post by bulldog on 2006-11-04
Well your distro is end of life I think.

Is it possible to upgrade to Dapper?

---

### Post by requiem_gr on 2006-11-04
And how you upgrade to Dapper, so I can try it?

---

### Post by bulldog on 2006-11-04
You can download the ISO from here,

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Maybe you could update online,but I prefer a clean install.
For update online you have to do a search by yourself.

---

### Post by requiem_gr on 2006-11-04
I can download it, but how will I burn it? I don't have any burning program working...

---

### Post by requiem_gr on 2006-11-04
Thank you all for your help and effort, but in the end this [post]("http://www.ncaabbs.com/forums/ncaa/phpbb/viewtopic.php?t=19271") saved the day.


Gnomebaker is up and running smoothly.

---

### Post by frediE on 2006-11-06
try using BinChunker it converts .bin files to .iso files then you should be set using GnomeBaker

sudo apt-get install bchunk

---

