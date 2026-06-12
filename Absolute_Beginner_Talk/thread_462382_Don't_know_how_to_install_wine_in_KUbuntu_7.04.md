---
title: "Don't know how to install wine in KUbuntu 7.04"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by L1nux01D on 2007-06-02
Hello everyone!Just installed Kubuntu 7.04 Fiesty Fawn.I had before Ubuntu 6.06,and it's a little difficult to move on KDE from Gnome.I want to ask:How to install wine?I can't install it from Konsole,and from Synaptic to.

Have any information?

---

### Post by kevdog on 2007-06-02
What happens when you just type in a Konsole box:

```

sudo aptitude update
sudo aptitude install wine

```

---

### Post by L1nux01D on 2007-06-02
sudo aptitude install wine
Password:
Reading state information... Complete
Initializing package states... Complete
Building tag database... Complete
No candidate version found for wine
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-common
  linux-restricted-modules-generic
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater amarok amarok-xine apport apport-qt hal
  hwdb-client-common hwdb-client-kde k3b kaffeine kaffeine-xine kate
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdepasswd kdeprint
  kdesktop kdm kfind khelpcenter kicker klipper kmenuedit konqueror
  konqueror-nsplugins konsole ksmserver ksplash ksysguard ksysguardd
  ktorrent kwin libfreetype6 libhal-storage1 libhal1 libk3b2 libkonq4
  libpq5 libpulse0 libsmbclient linux-generic linux-headers-generic python
  python-apport python-minimal python-problem-report python2.5
  python2.5-dev python2.5-minimal samba-common smbclient tzdata
  unattended-upgrades vim-common vim-tiny
0 packages upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Complete

---

### Post by bodhi.zazen on 2007-06-02
LOL

Looks like you need to add a few repositories, wine is in **Universe**

[http://packages.ubuntu.com/feisty/otherosfs/wine](http://packages.ubuntu.com/feisty/otherosfs/wine)

You can also see here : [http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by JordanII on 2007-06-02
Did you check the Package Manager?

~Jordan

---

### Post by L1nux01D on 2007-06-02
Thanks to everyone!!!I just installed wine (Don't know how I made it,but it work)!

---

