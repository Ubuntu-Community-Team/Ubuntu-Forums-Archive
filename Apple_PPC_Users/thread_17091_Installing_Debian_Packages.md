---
title: "Installing Debian Packages"
date: 2005-02-25
forum: Apple PPC Users
---

### Post by garmaniac on 2005-02-25
I an a new linux user and have recently been trying to use apt-get to install some of my favorite debian packages (since I heard ubuntu works with that) upon doing so I get this response in the terminal

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  digitaldj: Depends: maplay3 but it is not installable or
                      mpg123 or
                      amp but it is not installable
  libgnome32: Depends: gnome-libs-data (>= 1.2.13-5) but it is not going to be installed
  libgnomesupport0: Depends: gnome-libs-data (>= 1.2.13-5) but it is not going to be installed
  libgnomeui32: Depends: gnome-libs-data (>= 1.2.13-5) but it is not going to be installed
  libgnorba27: Depends: gnome-libs-data (>= 1.2.13-5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have run apt-get -f install with no results, what should I do

---

### Post by bored2k on 2005-02-25
looks like ur in need of some good repositories:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

---

### Post by gruepig on 2005-02-26
[QUOTE=bored2k]looks like ur in need of some good repositories:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse[/QUOTE]

Add the above lines to the file /etc/apt/sources.list, run 'apt-get update', and then try to install again.

---

### Post by farruinn on 2005-03-02
Please note, Ubuntu and Debian packages don't necessarily "mix" well.  If I absolutely must have something from Debian or Hoary, I try to use 'apt-get source'.  This way the package is built with Ubuntu libraries which sometimes help (granted sometimes it causes bigger problems, but this is the first thing I try).  This Debian Howto *is* helpful however: [http://www.nl.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.nl.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)  :lol: 

-Nathan

---

