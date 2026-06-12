---
title: "picking kubuntu brains..."
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-09-27
just found this

[http://tadspot.com/2005/12/30/howto-switching-from-ubuntu-to-kubuntu/](http://tadspot.com/2005/12/30/howto-switching-from-ubuntu-to-kubuntu/)

It all sounds fine but I wondered about going back afterwards if I don't like it.

Any hints?

---

### Post by halitech on 2006-09-27
no reason why you can't install KDE, XFCE Fluxbox or any one of the other desktops, try them and if you decide you don't like them, go into Synaptic and unistall them and stick with the one you like.

---

### Post by linear on 2006-09-27
Use aptitude at a command prompt:

[B]sudo aptitude install kubuntu-desktop
[/B]
Then you can reverse the process with:

[B]sudo aptitude remove kubuntu-desktop

[/B](Aptitude will keep track of everything installed; apt-get and Synaptic won't.)

---

### Post by Jareth on 2006-09-27
Ok, so what does the aptitude thing do, out of curiosity?

---

### Post by ewl1217 on 2006-09-27
If you haven't installed KDE yet, then install it with the following command at the terminal:
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```To remove KDE, and all the programs that came with it, use this command:
```
sudo aptitude remove kubuntu-desktop
```
If you've already installed KDE without using aptitude, however, you're out of luck. You'll have to uninstall it manually. Just use Synaptic to search for packages related to KDE and QT (the toolkit that KDE uses). A command-line tool called deborphan may be useful in removing unwanted programs and libraries added with the installation of KDE.

**EDIT:** Aptitude is a front-end to apt (Ubuntu's package management system), just like Synaptic. Aptitude remembers programs installed as requirements with other programs (called dependencies) and removes them at the removal of the original program you installed. For example, if you install a package called program, it may also require libprogram to be installed. If you uninstall program with aptitude (provided that you also installed it with aptitude) then libprogram will also be removed. This is useful with packages like kubuntu-desktop, which require **a lot** of dependencies.

---

### Post by Jareth on 2006-09-27
Super-lightning responses by the way!:p

---

