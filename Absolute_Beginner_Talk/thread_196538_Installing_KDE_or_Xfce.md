---
title: "Installing KDE or Xfce"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by CesarZ on 2006-06-14
Hello, I wanted to install Xfce or KDE. I followed [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html) instructions but I dont see the option in the Sessions windows to use KDE. But the KDE programs are install like Konqueror, Console.... 

I just dont know what is going on.

---

### Post by CesarZ on 2006-06-14
OK, little more info. Synaptic says: 
"Could Not Mark all packages for installation or Upgrades" 
the following packages have unresolvable dependencies. make sure that all required repositories are added and enabled in the preferences."

kubuntu-desktop:
 Depends: adept but it is not going to be installed
 Depends: amarok but it is not going to be installed
 Depends: ivman but it is not going to be installed
 Depends: k3b but it is not going to be installed
 Depends: kaudiocreator but it is not going to be installed
 Depends: kde-guidance but it is not going to be installed
 Depends: kdemultimedia-kfile-plugins but it is not going to be installed
 Depends: kdemultimedia-kio-plugins but it is not going to be installed
 Depends: kwin but it is not going to be installed
 Depends: openoffice.org2-kde but it is not going to be installed

I tried with aptitude install kubuntu-desktop and it does load some packs. but obviously no all of them. All repositories are enabled. you guys can help me out please? gracias.

---

### Post by aysiu on 2006-06-14
[QUOTE=CesarZ]All repositories are enabled.[/QUOTE] Maybe this is your problem. You may have some conflicting repositories in there.

I'd get a fresh list: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) and then try ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

