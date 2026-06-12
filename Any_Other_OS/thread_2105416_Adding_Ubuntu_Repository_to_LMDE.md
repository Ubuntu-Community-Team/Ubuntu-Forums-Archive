---
title: "Adding Ubuntu Repository to LMDE"
date: 2013-01-16
forum: Any Other OS
---

### Post by Zane Pepper on 2013-01-16
Is there any way I can do this? I want to install the Ubuntu theme and icons because I really like them, but I am having a hard time finding working versions of them on the web.

---

### Post by xenopeek on 2013-01-16
Perhaps elaborate a bit on what you mean? Unity isn't available on Debian, and hence not on LMDE, AFAIK (see stalled status of Unity port to Debian here: [http://wiki.debian.org/Ayatana/Packages](http://wiki.debian.org/Ayatana/Packages)). So at least Unity's theme you won't be able to use on LMDE with Cinnamon or MATE, or other desktop environment you have installed.

As for icons, perhaps that will work though I have no experience with changing icon sets. Ubuntu 12.10 is using the Humanity icon theme, which you can download as a .deb file from here: [http://packages.ubuntu.com/quantal/humanity-icon-theme](http://packages.ubuntu.com/quantal/humanity-icon-theme). The two dependencies it has (gnome-icon-theme and hicolor-icon-theme) should be satisfiable on LMDE with UP6.

---

### Post by Zane Pepper on 2013-01-16
In regular Linux Mint I would open Synaptic and search "light-themes" and install that, But it is not on LMDE, so I assume it is part of the Ubuntu repository.

---

### Post by xenopeek on 2013-01-16
I already linked you to the Ubuntu packages website, so you can search there for any packages from Ubuntu that you want, and download them to try and install them on LMDE. light-themes will need humanity-icon-theme and ubuntu-mono from there also. The other dependencies should be satisfiable on LMDE.

---

### Post by Zane Pepper on 2013-01-16
Sorry, I was not really paying attention. I had just woken up when I posted that lol. I will download the packages and tell you if they worked or not.

---

