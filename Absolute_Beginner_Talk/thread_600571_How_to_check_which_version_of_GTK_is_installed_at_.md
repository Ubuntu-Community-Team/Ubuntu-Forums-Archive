---
title: "How to check which version of GTK is installed at KUBUNTU 7.10 ?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by slobodan on 2007-11-02
How to check which version of GTK is installed at KUBUNTU 7.10 ?
I need something like 
rpm -q gtk2

thanks
Slobodan

---

### Post by g2g591 on 2007-11-02
just open up adept and click on the down arrow thing for the package (or if you want a terminal command, try apt-cache showpkg libgtk2 ) (not sure exactly the name of the gtk package)

---

### Post by slobodan on 2007-11-02
just open up adept and click on the down arrow thing for the package

You mean adept-installer from Add Remove programs, any arrow there is chosing AnySuite/KDE/Gnome  I have Ubuntu isntalled too.

 (or if you want a terminal command, try apt-cache showpkg libgtk2 ) (not sure exactly the name of the gtk package)
bobi@bobi-desktop:~$ apt-cache showpkg libgtk2 
W: Unable to locate package libgtk2

---

### Post by argie on 2007-11-02
```
apt-cache search libgtk
```
That'll find your package name. Mine is libgtk2.0-0 so I'll do this, you'll have to substitute the right one: (replace the bold part, if you only have gtk1.2 you'll check that, but it's probably gtk2)
```
apt-cache showpkg **libgtk2.0-0** | more 
```
Piping it through more because the list of things that depend on it is very big and will be hard to scroll through.

---

### Post by slobodan on 2007-11-02
Thank you Argie
I got below. I need GTK 2.4 or better for one application .
 Did i have it or I need to install it and how?
 
bobi@bobi-desktop:~$ apt-cache showpkg libgtk2.0-0 | more    
Package: libgtk2.0-0
Versions: 
2.12.0-1ubuntu3 (/var/lib/apt/lists/ubuntu.linux-bg.org_ubuntu_dists_gutsy_main_
binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/ubuntu.linux-bg.org_ubuntu_dists_gutsy
_main_binary-i386_Packages
                  MD5: 3ed10be69b676a812afff2c7fdaa4017


Reverse Depends: 
  xvidcap,libgtk2.0-0 2.10.3
  adobereader-enu,libgtk2.0-0 2.4
  audacious-plugins-extra,libgtk2.0-0 2.12.0
  audacious-plugins,libgtk2.0-0 2.12.0
  thunderbird-gnome-support,libgtk2.0-0 2.12.0
  thunderbird,libgtk2.0-0 2.12.0
  gnome-screensaver,libgtk2.0-0 2.12.0
  firefox-gnome-support,libgtk2.0-0 2.12.0
  firefox,libgtk2.0-0 2.12.0
  iceape-gnome-support,libgtk2.0-0 2.12.0
  iceape-browser,libgtk2.0-0 2.12.0
  xvid4conf,libgtk2.0-0 2.10.3

---

### Post by zvacet on 2007-11-02
[http://www.gtk.org/]("http://www.gtk.org/")

---

### Post by argie on 2007-11-03
You have version 2.12.0, that's greater than 2.4. Perhaps if you tell us what program you are trying to run we'll be able to help.

---

### Post by slobodan on 2007-11-06
You have version 2.12.0, that's greater than 2.4. Perhaps if you tell us what program you are trying to run we'll be able to help.

Thanks again argie. The program is ACL,  but I'll take care about it from now.

cheers
Slobodan

---

