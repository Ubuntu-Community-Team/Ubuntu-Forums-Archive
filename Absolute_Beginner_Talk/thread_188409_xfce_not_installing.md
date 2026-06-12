---
title: "xfce not installing"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-06-04
sudo apt-get can't install xfce for me

ejaz@msiddique:~$ sudo apt-get install xubuntu-desktop
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
  xubuntu-desktop: Depends: thunar but it is not going to be installed
                   Depends: thunar-media-tags-plugin but it is not going to be installed
                   Depends: xfce4-session but it is not going to be installed
                   Depends: xfce4-terminal but it is not going to be installed
                   Depends: xfce4-utils but it is not going to be installed
                   Depends: xfdesktop4 but it is not going to be installed
                   Depends: xfmedia but it is not going to be installed
E: Broken packages

---

### Post by TrendyDark on 2006-06-04
try just installing XFCE. . .


```
sudo apt-get install xfce
```

I'm not sure if that works, because I'd never tried it, but I know it works for KDE.

---

### Post by aysiu on 2006-06-04
Sounds as if you have conflicting repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then follow these directions to install XFCE:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by u04f061 on 2006-06-04
[QUOTE=aysiu]Sounds as if you have conflicting repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then follow these directions to install XFCE:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)[/QUOTE]

thnx.problem was with list

---

