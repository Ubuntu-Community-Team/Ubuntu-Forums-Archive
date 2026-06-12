---
title: "Help with installing kdenlive, please? :)"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-16
I'm trying to install [kdenlive](http://kdenlive.sourceforge.net/) but I'm having a bit of trouble. The downloads page does show a debian repository address, so I added that to my list and attempted to install, but came up with a no-go. Terminal reports this:

```
The following packages have unmet dependencies:
  kdenlive: Depends: kdelibs4c2a (>= 4:3.5.4-1) but 4:3.5.2-0ubuntu18.1 is to be installed
            Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
            Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
            Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
            Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
            Depends: libiec61883-0 but it is not installable
            Depends: libmlt++0 (>= 0.2.0) but it is not going to be installed
            Depends: libmlt0 (>= 0.2.0) but it is not going to be installed
            Depends: libraw1394-8 but it is not installable
            Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
E: Broken packages
```

As you can see, most of the packages are already installed through ubuntu, but are a lower version than needed. I need to upgrade these somehow, but they aren't in synaptic to be able to do so.

How would I go about getting the depencies in my system so I can use the app? :)


(PS. Overall I need an app which can edit .mpg files for my class in school. I chose kdenlive because of it's excellent GUI and useability (from what I've seen). If you have any other application suggestions to replace kdenlive, feel free to suggest them.)

:D

---

### Post by UnknownVariable on 2006-10-17
Bumping this once before school. :) If you guys could recommend another video editing software instead, that'd be great, as I kinda need one asap.

---

### Post by Bachstelze on 2006-10-17
Apparently, you want to install the version of kdeenlibs for KDE 3.5.4 but you currently have 3.5.2 installed. You can either try to install kdeenlibs for KDE 3.5.2 or upgrade to KDE 3.5.4. Instructions for upgrading are [here](http://kubuntu.org/announcements/kde-354.php) - and [here](http://kubuntu.org/announcements/kde-355.php) for KDE 3.5.5.

Well, actually I don't think you'll be able to install that package under Dapper since it uses libs that are not in it's repos, you'll neet to upgrade to Edgy.

---

