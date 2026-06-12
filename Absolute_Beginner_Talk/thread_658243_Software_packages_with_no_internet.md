---
title: "Software packages with no internet?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by desertphotog on 2008-01-04
So... my New Year's resolution was to turn my back on MS and go with a LInux setup.  All went well with a clean install on my Dell Inspiron 9200.  WiFi works in the city, but there are none broadcasting where I am.  How do you install/update software Packages if the Unbutu machine isn't on line?  Can they be saved somehow on a cd from another machine?

---

### Post by steeleyuk on 2008-01-04
Anything that APT downloads is stored in /var/cache/apt/archives as a .DEB file. You can copy these to a disk and install them on a machine without an internet connection. Though, theres a chance that some dependencies will be missing.

---

### Post by pieterjanvu on 2008-01-04
There should be some software updates and packages on the ubuntu cd, however, considering you probably installed from there, most of the software is the same version. You might find some additional software packages on the cd. you could also download the ubuntu DVD there may be more software packages there.

---

### Post by ugm6hr on 2008-01-04
> **desertphotog said:**
> So... my New Year's resolution was to turn my back on MS and go with a LInux setup.  All went well with a clean install on my Dell Inspiron 9200.  WiFi works in the city, but there are none broadcasting where I am.  How do you install/update software Packages if the Unbutu machine isn't on line?  Can they be saved somehow on a cd from another machine?

I would recommend you use this:
[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

It is explained here:
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by dannyboy79 on 2008-01-04
aptoncd is a super cool app. you can go to any location that you have an internet connection and a dvd-burner and an additional cd-rom, run a livecd, install aptoncd, then run it.

[http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html](http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html)

the cd that you used to install ubuntu with will have a lot of the apps already on it and you can install from there. if it's not on there, you can download individual .deb's from the internet. just do a search. a lot of them will be here: [http://www.getdeb.net/](http://www.getdeb.net/)

or, if you're using Feisty fawn, you can download the entire repo onto a dvd from here:
[http://blog.mypapit.net/2007/07/ubuntu-feisty-fawn-repository-on-dvd.html](http://blog.mypapit.net/2007/07/ubuntu-feisty-fawn-repository-on-dvd.html)
(that's if it's still there on that ftp site)

good luck

---

### Post by desertphotog on 2008-01-04
Thanks to all -  I knew there must be a way!  Does any one know of a high end photo editor other than the GIMP?  By the way, it is Gutsy and I love it .

---

### Post by steeleyuk on 2008-01-04
You could try [Krita]("apt://krita"). Its a KDE application however but it will still install fine on GNOME. Not quite sure if it has as many features as GIMP either, but its worth a try.

---

### Post by dannyboy79 on 2008-01-04
well if you're talking about commercially available apps, Photoshop CS2 works in WINE.


[http://ubuntuforums.org/showthread.php?t=275488&page=7](http://ubuntuforums.org/showthread.php?t=275488&page=7)

---

