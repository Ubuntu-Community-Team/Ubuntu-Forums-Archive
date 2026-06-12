---
title: "How to install KDE on Ubuntu PPC"
date: 2004-11-07
forum: Apple PPC Users
---

### Post by ys` on 2004-11-07
I just installed ubuntu warty on my PowerBook G4 and I'm trying to install KDE, but I'm have problems.

# apt-get install kde
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
kde: Depends: kde-core but it is not going to be installed
Depends: kde-amusements but it is not going to be installed
Depends: kdeaddons but it is not going to be installed
Depends: kdeadmin but it is not going to be installed
Depends: kdeartwork but it is not going to be installed
Depends: kdegraphics but it is not going to be installed
Depends: kdemultimedia but it is not going to be installed
Depends: kdenetwork but it is not going to be installed
Depends: kdepim but it is not going to be installed
Depends: kdeutils but it is not going to be installed
Depends: quanta but it is not installable
E: Broken packages

My source.list is:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb [http://jrfonseca.dyndns.org/debian](http://jrfonseca.dyndns.org/debian) ./
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

What should I do?

---

### Post by sgiunchi on 2004-11-08
As far as I know, KDE on UBUNTU PPC doesn't work for failed dependencies.
I asked in the forum few days ago, and the answers I got confirm this.

Sorry

---

### Post by TekMate on 2004-11-08
Yes it appears to be a bug hopefully this will be fixed soon. I like Gnome but there are some KDE apps I just can't do without.

---

### Post by moly82 on 2004-11-09
i was able to install kde on ubuntu, just inserting the debian sid repositories inside /eta/apt/sources.list

then apt-get install kdebase

it works fine here, then you can also remove the above-mentioned repositories if you like ;) :p

ciao!

---

### Post by carg on 2005-01-07
Moly82,
I am new in this.
I am trying to make KDE work in Ubuntu. I managed to install it but I don't know how can I run it.
Also, do you know how to change GNOME for KDE at start up?


[QUOTE=moly82]i was able to install kde on ubuntu, just inserting the debian sid repositories inside /eta/apt/sources.list

then apt-get install kdebase

it works fine here, then you can also remove the above-mentioned repositories if you like ;) :p

ciao![/QUOTE]

---

### Post by tiiim on 2005-01-07
[QUOTE=carg]Moly82,
I am new in this.
I am trying to make KDE work in Ubuntu. I managed to install it but I don't know how can I run it.
Also, do you know how to change GNOME for KDE at start up?[/QUOTE]
 isnt under the sessions on the login screen? if not there be a config file somewhere you add it... which im sure someone will let you know now...

---

