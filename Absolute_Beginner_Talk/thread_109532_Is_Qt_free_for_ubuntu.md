---
title: "Is Qt free for ubuntu?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-12-28
If it is free, how can i get it installed on my computer?

---

### Post by glacierre on 2005-12-28
QT the library of trolltech (best known as the core of kde), or QT (quicktime) the apple codec?

---

### Post by racermike1967 on 2005-12-28
QT the library of trolltech

---

### Post by az on 2005-12-29
Search synaptic for libqt.  They are all there.

They are dual-licenced.  One of the licences is GPL (or gpl-compatible) which is why they are available to ubuntu in the main repository.  A long while ago, they were non-free and recently, only the windows version had restrictions (you could not distribute an app you made with it commercially without getting a licence from them to do so - or something like that)

It's hard to beleive that years ago, there were no X servers available as free software - you had to pay to get a working X server....  FLOSS has come a long way...

---

### Post by davidsrsb on 2005-12-29
The QT licence in the past was not GPL, which lead to the KDE vs Gnome religious wars. These days QT on Linux is GPL compatible. The permission to use on Windows for GPL purposes is another more recent change, previously any Windows software required a paid for licence. This is why KDE on Windows is now possible.

---

### Post by grim918 on 2005-12-29
if you want to get qt installed on ubuntu just:

sudo apt-get install qt3-designer libqt3-mt-dev qt3-dev-tools

this should get you going. it will install the qt3 ide along with everything else that you might need. its free no need to pay anything. i think that there is already qt4 but i dont know if its available on ubuntu.

---

### Post by grim918 on 2005-12-29
almost forgot. once you install qt3-designer just type in 
designer    at a command prompt. this should launch qt3 designer.

---

### Post by Bubbasheeko on 2006-02-02
Tried to run this and received this message:

root@slave:/usr/local # sudo apt-get install qt3-designer libqt3-mt-dev qt3-dev-tools
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package qt3-designer

Any assistance??

---

### Post by Lord Illidan on 2006-02-02
Have you enabled all the repositories? Give us your /etc/apt/sources.list .

Second, to search for a package from the command line, do this:

```
sudo apt-cache search *package*
``` (without asterisks)

---

### Post by az on 2006-02-02
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Adding%29%7C%28Repositor%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Adding%29%7C%28Repositor%29)

---

### Post by Bubbasheeko on 2006-02-02
This is from sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


When I attempted to search, this is all I received:

root@slave:/usr/local # sudo apt-cache search qt3-designer
root@slave:/usr/local # 

Anything else?  Thanks for the quick reply.

---

### Post by Bubbasheeko on 2006-02-02
azz,

Added the repositories, but still nothing.

libqte-mt3-dev:
 Depends: qt3-dev-tools  but it is not installable
 Depends: libpng12-0-dev  but it is not installable
 Depends: libjpeg62-dev  but it is not installable or
 	libjpeg-dev  but it is not installable
 Depends: libmng-dev  but it is not installable

---

### Post by Matt Smith on 2006-03-18
[QUOTE=davidsrsb]The QT licence in the past was not GPL, which lead to the KDE vs Gnome religious wars. These days QT on Linux is GPL compatible. The permission to use on Windows for GPL purposes is another more recent change, previously any Windows software required a paid for licence. This is why KDE on Windows is now possible.[/QUOTE]

In fact, the religious wars were caused by KDE using early versions of Qt which were not open-source at all.  They were released under a special licence which allowed their *use* in open-source products, but did not match the criteria for being open-source (I think not allowing modification was the sticking point).  The religious wars abated when the QPL, which is a genuine open-source licence, came into being.

It is only Qt4 which is available open-source on Windows.  Qt3, including recent updates, is open-source only on X11 and Mac.  So there will be no KDE for Windows until KDE4 is out.

---

