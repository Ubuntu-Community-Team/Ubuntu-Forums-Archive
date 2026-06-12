---
title: "Xorg dependencies"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by juantovarm on 2007-04-08
I want to install Xorg.dev but i get this problem:

xorg-dev:
 Depends: libxss-dev but it is not going to be installed

When i try to install libxss-dev i get this problem:

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all requiered repositories are added and enabled in the preferences

libxss-dev:
  Depends: libxss1 (=1:1.0.1-4ubuntu1) but 1:1.1-0ubuntu1 is to be installed

And of course they are added AND enabled.

Any ideas? :confused:

---

### Post by WiseElben on 2007-04-08
Your libxss1 version is too low, so you'll need to either compile it from source or find a deb that is a higher version.

---

### Post by zvacet on 2007-04-08
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxss1&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxss1&searchon=names&subword=1&version=edgy&release=all")

---

### Post by threegremlins on 2007-04-08
A lot of people are big on apt-get but I prefer to use Synaptic. I'm not sure if you can but if you've been able to get to the Gnome desktop start Synaptic and click on settings at the top, then repositories when the window opens up look for or add repositories, add them all. Then close and click on reload, hopefully you'll be able to find the lib your looking for. If this doesn't help then someone who knows more will respond shortly.
Dave

In the time it took me to write this two people got in ahead of me

---

### Post by zvacet on 2007-04-08
Forget about link I posted to you.Go to the FF search engine and under Ubuntu packages type name of packages you are looking for.You will find package and all dependencies.If you want to avoid this type of situation in the future install packages with 
```
sudo aptitude install package_name
```

This command install package andall dependencies.

---

