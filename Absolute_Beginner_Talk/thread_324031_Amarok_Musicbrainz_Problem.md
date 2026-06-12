---
title: "Amarok Musicbrainz Problem"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by pipin on 2006-12-23
Hello. When i try to tag my mp3s with musicbrainz; it doesn't work , with no error massage . I am Edgy gnome user. Thanks

---

### Post by jordanmthomas on 2006-12-23
Do you have libtag installed?
```
sudo aptitude --reinstall install libtag
```
It's probably a requesite for amarok anyway, but it is what does the work when tagging mp3s, not musicbrainz.

See if this might help?

**oh, I think I know what you are getting at...maybe reinstall any packages related to musicbrainz?
```
apt-cache search musicbrainz
```
I don't use ubuntu so I am not sure of the exact package name.

Maybe installing amarok from source could work too.

---

### Post by pipin on 2006-12-23
mkdir libtunepimp
cd lintunepimp
apt-get source libtunepimp
cd libtunepimp*
fakeroot dpkg-buildpackage

I used this guide of wiki but fakeroot doesnt work properly. Terminal messages
> dpkg-buildpackage: source package is libtunepimp
dpkg-buildpackage: source version is 0.4.2-3ubuntu3
dpkg-buildpackage: source changed by Jonathan Riddell <jriddell@ubuntu.com>
sh: gcc: not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.4.2-3ubuntu3
sh: gcc: not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-checkbuilddeps: Unmet build dependencies: cdbs dh-buildinfo libmad0-dev libid3tag0-dev libogg-dev libvorbis-dev libflac-dev (>= 1.1.2-1) libmusicbrainz4-dev (>= 2.1.1-3.1) zlib1g-dev libncurses5-dev libreadline5-dev | libreadline-dev zlib1g-dev doxygen docbook-to-man python2.4-dev python-dev libexpat1-dev libtag1-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)


---

### Post by pipin on 2006-12-24
Hi. Please help. How can I use tagging option of Amarok? 

 I have installed fakeroot but I cant get deb file according to the instructions of Wiki below.
> mkdir libtunepimp
cd lintunepimp
apt-get source libtunepimp
cd libtunepimp*
fakeroot dpkg-buildpackage

when I use **fakeroot dpkg-buildpackage** the terminal says 
> dpkg-buildpackage: source version without epoch 0.4.2-3ubuntu3
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5) cdbs dh-buildinfo libmad0-dev libid3tag0-dev libogg-dev libvorbis-dev libflac-dev (>= 1.1.2-1) libmusicbrainz4-dev (>= 2.1.1-3.1) libncurses5-dev libreadline5-dev | libreadline-dev doxygen docbook-to-man python-dev libtag1-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)


and aborts the process. How can I solve it? Or forget about it, how can I use tagging facility in Ubuntu?

---

