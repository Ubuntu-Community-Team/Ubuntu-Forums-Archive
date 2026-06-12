---
title: "HELP me"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by xxyper on 2007-05-24
Im an absolute newbie to linux but have gotten myself in quite the quandary, I seem to have played with the packages a little too much, and now I have know "widgets" i think they're called, no real graphical user interface. i guess trying to decide on either kde or gnome and switching between the packages ive screwed something up and im not sure what! I really dont want to reformat and try again If anyone can help it would be greatly appreciated and i could return the favor with technical knowledge of the security industry priv and gov sects.  And then maybe someone could point me in the direction of some linux gurus in new jersey, USA so that i cant begin furthering my security skills

---

### Post by revealer on 2007-05-24
> **xxyper said:**
> i could return the favor with technical knowledge of the security industry priv and gov sects.  And then maybe someone could point me in the direction of some linux gurus in new jersey, USA so that i cant begin furthering my security skills

WTF?????

---

### Post by lazyart on 2007-05-24
sudo apt-get install ubuntu-desktop

Log out and in again... that might help.

---

### Post by ryanVickers on 2007-05-24
> sudo apt-get install ubuntu-desktop

yes, that will install gnome.  if you want the kde, same thing but "kubuntu-desktop".

You may have to resart for this to take effect, but probably not.  if the login manager is screwed up, do sudo dpkg-reconfige gdm

"gdm" can be replaced with "kdm" if you want the kde one (login manager)

Just switching between kde and gnome wouldn't do that though, you must have done something else by accident. Just so you know, you don't have to reinstall to switch back and forth, just pick "KDE" or "GNOME" before you logon :p

---

