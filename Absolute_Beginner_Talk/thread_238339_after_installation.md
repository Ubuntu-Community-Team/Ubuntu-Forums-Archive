---
title: "after installation"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-08-17
i have just finished installing the alternate desktop version of ubuntu and i have logged in with my account but im still in text mode. how do i get a gui?? i am supposed to type something but i have no clue what.

---

### Post by taurus on 2006-08-17
See what happens if you type this at the prompt, after you log in...

```

startx

```
If you get an error about command not found, then you need to install a window manager like

```

sudo apt-get update
sudo apt-get install ubuntu-desktop <-- for Gnome
sudo apt-get install kubuntu-desktop <-- for KDE
sudo apt-get install xubuntu-desktip <-- for XFce4

```

---

### Post by sean_ on 2006-08-17
If you're really new to ubuntu, you don't have to do all of them, you're able to choose one.

---

### Post by k94382 on 2006-08-17
wow it actually worked for me! thanks guys. now one more question. i have installed the gui for xubuntu and now i have decided that i want gnome. how do i uninstall xfce (i think) and use gnome instead??

---

### Post by Perfect Storm on 2006-08-17
Meh, you better have done the installation with aptitude then.

like:
```
sudo aptitude install xubuntu-desktop
```

Then you could have done this:

```
sudo aptitude remove xubuntu-desktop
```

Aptitude is good when you are installing a package which have huge dependecy and then want to remove them all again.

---

### Post by catlett on 2006-08-17
To remove xubuntu, run ```
sudo apt-get remove xubuntu-desktop
``` A.I. is referring to the fact that apt-get will not track all the dependencies when installing a package. So now when you run apt-get remove, some packages installed during xubuntu-desktop will be left on your system doing nothing.
 Hopefully aptitude will find then. It does for me. When I run an aptitude upgrade it will remove packages that do "nothing".
Anyways, do this for gnome and to see if aptitude can take care of the issue
```
sudo aptitude install ubuntu-desktop
```
```
sudo aptitude update
```
```
sudo aptitude upgrade
```Hopefully it will notice the left over packages from xubuntu and remove them. 
You will now have the ubuntu regular installation, which is the gnome desktop. If you have enough disk space, you can leave xubuntu installed and install ubuntu-desktop alongside it.  All you do to change from one to the other is select "options" at tbe login screen and then select "change session". Then you can either select xfce or gnome as your desktop for that session.

---

