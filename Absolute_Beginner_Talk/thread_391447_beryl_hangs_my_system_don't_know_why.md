---
title: "beryl hangs my system don't know why"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by skidkid87 on 2007-03-23
help me out plz

I've installed beryl for a couple of days now there were a few bugs but I dealt with them (if u call logging out and in again dealing with it) and today when I checked the box in shimmering window or something like that in the beryl manager linux hanged and I tried completely removing and reinstalling but that didn't work, every time I launched beryl the system hanged

I'm running ubuntu 6.10 edgy eft in KDE environment and my graphcs driver is nvidia 6200 GeForce

when I completely remove beryl from synaptic package manager these 2 lines appear (in the middle of other successful tasks):

dpkg - warning: while removing beryl-core, directory '/usrshare/locale/de_DE/LO_MESSEGES' not empty so not removed
dpkg - warning: while removing beryl-core, directory '/usrshare/locale/de_DE' not empty so not removed

I think think that's what's keeping the configurations that hang my system every time I run beryl 

help me out plz

PS: I'm a n00b just have ubuntu for a few weeks so please be specific

---

### Post by wpshooter on 2007-03-23
Suggestion.  Do a search on the Beryl program in these forums and see how many similiar post to yours that you find.  Does that tell you anything ?

---

### Post by skidkid87 on 2007-03-23
these problems aren't similar to mine

it used to work fine before I selected that option and now it doesn't work 

and about the other problems; it only tells me that beryl is not stable that's all

---

### Post by wyrfel on 2007-05-06
Try this:

- exit beryl
- open a terminal
- type: gconftool-2 -u --recursive-unset /apps/beryl
- enter
- restart beryl

if that doesn't work, try deleting the settings via: rm -R .gconf/apps/beryl
and restart you whole gnome-session.

AFAIK, uninstalling beryl will not delete your settings.

André.

---

