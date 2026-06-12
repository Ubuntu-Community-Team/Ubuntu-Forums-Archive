---
title: "Window Manager in Ubuntu"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by sankarv on 2006-08-02
Does Ubuntu has any other Window manager other than GNome in its install CD?
If so what are they? How to install them in setup

---

### Post by jimmygoon on 2006-08-02
> **sankarv said:**
> Does Ubuntu has any other Window manager other than GNome in its install CD?
If so what are they? How to install them in setup

You could have install kubuntu (kde) or xubuntu (xfce) but I prefer to use ubuntu, and then later either intall kubuntu-desktop or kde from the terminal.

people will tell you that kubuntu-desktop is better but I found that when I used it, it replaced SO much stuff like my boot-splash, login, gtk+ skin(??) and all kinds of stuff... to the point where I was just.... screw it, and reloaded

---

### Post by sankarv on 2006-08-02
So you mean the Ubuntu CD has either Gnome/KDE/Xfce and not any other Window managers?

---

### Post by 3rdalbum on 2006-08-02
The Ubuntu CD has Metacity, and no other window managers.

The Kubuntu CD has KWM, and no other window managers.

The Xubuntu CD has XFWM, and no other window managers.

However, by using Synaptic, you can install lots of other window managers and Desktop Environments... everything from IceWM to Enlightenment to Window Maker to Compiz!

---

### Post by Uncle Spellbinder on 2006-08-02
> **sankarv said:**
> So you mean the Ubuntu CD has either Gnome/KDE/Xfce and not any other Window managers?

Ubuntu = Gnome
Kumuntu = KDE
Xubuntu = Xfce

---

### Post by 5-HT on 2006-08-02
> **sankarv said:**
> So you mean the Ubuntu CD has either Gnome/KDE/Xfce and not any other Window managers?

Correct. Ubuntu CD comes only  with GNOME, Kubuntu with KDE, and Xubuntu with XFCE. However, all three desktop environments, in addition to many window managers, are available in the repositories.

EDIT: beaten to it.

---

### Post by sankarv on 2006-08-02
so you mean we need to have active internet connection so that it automatically installs window managers from synaptic?

---

### Post by 5-HT on 2006-08-02
> **sankarv said:**
> so you mean we need to have active internet connection so that it automatically installs window managers from synaptic?

That would be the easiest way.
Alternatively, you could download the packages along with all dependencies from [http://packages.ubuntu.com](http://packages.ubuntu.com) on a computer with internet access, get them on the *buntu computer and install them with dpkg.

```
 sudo dpkg -i <path_to_.debs>
``` 
However, if you're dealing with large packages that have many dependencies (like  any of the *buntu-desktop packages), it can be a pain to manually download and install them in this manner.

---

### Post by sankarv on 2006-08-02
Thats fine. Thankx for the replys.

---

