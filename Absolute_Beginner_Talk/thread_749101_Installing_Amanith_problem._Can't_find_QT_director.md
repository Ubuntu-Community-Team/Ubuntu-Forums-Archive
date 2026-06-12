---
title: "Installing Amanith problem. Can't find QT directory"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Mr T 87 on 2008-04-08
I'm in the process of trying to get the Amanith framework on my installation of ubuntu. I'm following the tutorial [here]("http://www.amanith.org/tutorials/index.php").
 At step 2a it asks me to add this to my ~./profile file.
```
QTDIR=/usr/local/qt
MANPATH=$QTDIR/doc/man:$MANPATH
PATH=$QTDIR/bin:$PATH
AMANITHDIR=/home/frank/amanith
LD_LIBRARY_PATH=$QTDIR/lib:$AMANITHDIR/lib:$LD_LIBRARY_PATH
export AMANITHDIR QTDIR PATH MANPATH LD_LIBRARY_PATH
```
I've changed the AMNITHDIR to the correct location of my amanith files and this seems to be ok. The problem I have is with the QTDIR path. I can't find any folders anywhere for 'qt'. I have installed everything I could find in synaptic that had part of the name as something like qt3 or qt4.

I installed the qt3-dev-tools package using apt-get. Their is a folder under 'usr/lib/' called qt4 which only contains one folder labelled 'plugins'. I doubt this is the folder I'm after though. Any help getting this to work would be awesome. Stupid-proof help would be awesomer cause I am quite new to Ubuntu.

Thanks in advance :)

---

### Post by thewho? on 2008-04-14
You might try using libqt4-core.  [http://packages.ubuntu.com/edgy/libqt4-core](http://packages.ubuntu.com/edgy/libqt4-core)  I seems like you are missing the actual QT binaries.  You might try using apt-get install qt.

---

