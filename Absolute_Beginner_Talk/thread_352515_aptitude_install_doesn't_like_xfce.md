---
title: "aptitude install doesn't like xfce?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by d4ndy on 2007-02-03
Ubuntu 6.06 here.
Lately, when I try to install various things through "aptitude install," in the terminal, I always get this:

> The following packages are unused and will be REMOVED:
  abiword abiword-common abiword-help abiword-plugins anthy
  gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce
  libaiksaurusgtk-1.2-0c2a libanthy0 libchewing-data libchewing2
  libenchant1c2a libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-1-common
  libgoffice-gtk-1-2 libgtkmathview0c2a libots0 libtagc0 libthunar-vfs-1
  libwpd-stream8c2a mousepad orage scim-anthy scim-chewing scim-hangul
  scim-pinyin thunar thunar-media-tags-plugin w3c-dtd-xhtml xarchiver
  xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-fsguard-plugin xfce4-icon-theme
  xfce4-mailwatch-plugin xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin
  xfce4-netload-plugin xfce4-panel xfce4-quicklauncher-plugin
  xfce4-screenshooter-plugin xfce4-session xfce4-systemload-plugin
  xfce4-taskmanager xfce4-utils xfce4-verve-plugin xfce4-weather-plugin
  xfce4-xkb-plugin xfdesktop4 xfmedia xfprint4 xubuntu-artwork-usplash
  xubuntu-docs

and then it asks me if I want to proceed. Well, I'm using Xubuntu and quite happy with it. Am I just being offered the option of trimming out some already-used/no-longer-needed installation packages, or to actually uninstall programs? (I've been opting out and using Synaptic to install what I've been wanting) I'm inclined to think it's just leftover installation packages that are at risk here, but I thought I'd ask here before I toss out all my xfce.:(

---

### Post by jvc26 on 2007-02-10
Do you have Ubuntu installed and have installed the xubuntu-desktop package or have you installed Xubuntu from the word go?
Il

---

### Post by d4ndy on 2007-03-06
I started with a Dapper Ubuntu install, then later added the Xubuntu package; I still have the option of either/or Ubuntu/Xubuntu sessions, but I've been favoring Xubuntu on my aging desktop machine.

(Sorry for the seeming abandonment of the thread -- I checked back a number of times and saw no reply for a number of days, and since it's more a matter of curiosity than urgency, I guess I just forgot about it by the time you replied.)

I'm thinking I might just plunge in and allow the package-removal, just to see what happens.  The worst? A long session of re-installation.  And a message I consider somewhat ambiguous will be disambiguated.

---

### Post by melancholeric on 2007-03-06
I believe that's a bug in aptitude.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=299009](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=299009)

---

### Post by d4ndy on 2007-03-07
Oh, my gosh! It looks like it would have uninstalled all those goodies! Glad I held off.
I guess it pays to read the fine print before you sign (as it were).  :)

---

### Post by louieb on 2007-03-07
Thanks for the link. Yea its a bug I had Ubuntu and the kUbuntu-Desktop installed.  I did not read the fine print when installing some package and most of kUbuntu was removed. I rarely used KDE and at the time it did not bother me.** I read the fine print now when using aptitude.**

---

