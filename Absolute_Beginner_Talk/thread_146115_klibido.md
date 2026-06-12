---
title: "klibido"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by babwe on 2006-03-17
pls if any could assist to get klibido back up running again. 
running into this problem when I do ...........
sudo apt-get install klibido
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
  klibido: Depends: kdelibs4 (>= 4:3.3.2-6.2) but it is not installable
           Depends: libdb4.3++ but it is not installable
           Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
E: Broken packages

If someone could pls give me a rundown HOWTO get klibido running again

---

### Post by Brunellus on 2006-03-17
sudo apt-get -f install

that'll try to resolve your broken packages.

---

### Post by babwe on 2006-03-17
dident do the the trick
still getting this after
sudo apt-get -f install
then doing 
sudo apt-get install klibido
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
  klibido: Depends: kdelibs4 (>= 4:3.3.2-6.2) but it is not installable
           Depends: libdb4.3++ but it is not installable
           Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable

my sources.list is like this Is there something missing
deb file:/var/cache/apt-build/repository apt-build main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe $deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted unive$
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-f$deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free n$
##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted univers$## created by arniebackports

##deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
##deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

##deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
##deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

##deb [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./
##deb-src [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./

deb [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./
deb-src [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./

anything I need more in there

---

### Post by babwe on 2006-03-18
problem solved
heres the answer
sudo apt-get build-dep klibido

and whola It runs

---

