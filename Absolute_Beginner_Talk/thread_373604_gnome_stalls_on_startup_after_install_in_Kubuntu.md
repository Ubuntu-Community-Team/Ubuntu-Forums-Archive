---
title: "gnome stalls on startup after install in Kubuntu"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by niki001 on 2007-03-01
Hi,

I'm trying to widen my experience in Kunbuntu by trying out lots of stuff. KDE performed quit well for me, however I want to have a taste to gnome without having to loose all my settings etc. in KDE.
In installed gnome-desktop via synaptic. Kept KDM as default and performed a reboot from my session. At the menu in my login-screen i choose gnome in stead of kde to log in.
After typing my password and entering I get a brief  start of the 'Ubuntu'-splash but it stalls with the 'window-manager'-icon on it. Further nothing happens. When I press ALT-F2 I'm able to start in Ubuntu in save mode. Graphics mode doesn't seem to work.
Can anybody give me a tip on what could be wrong.
thx

---

### Post by jimbren on 2007-03-01
it sounds to me like the installation didn't go completely.  i would switch to a console (CTRL+ALT+F1) when you get to the login screen and do:
```
sudo apt-get update
```
then
```
sudo apt-get -f install
```
to fix any broken packages
then
```
sudo apt-get ubuntu-desktop
```
again, just for kicks.

---

### Post by niki001 on 2007-03-03
thx Jimbren,

that seemed to be the trick...

One prob left, Gnome starts up terribly slow. Could it be because gdm isn't set as default or is it due to another setting?

---

