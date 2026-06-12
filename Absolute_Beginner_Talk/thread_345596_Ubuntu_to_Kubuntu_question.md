---
title: "Ubuntu to Kubuntu question"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2007-01-24
I stumbled on [this site]("http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50") which has some neat Ubuntu tips.

One of the tips is:

 > 6. Adding a new desktop

Many users aren't sure what packages to add in order to run KDE or Xfce window managers on a stock Ubuntu system -- or what packages to add to run GNOME on Kubuntu or Xubuntu. You could add all of the necessary packages one at a time, but there's a much easier way to go about it.

To install all of the packages that come with one of the flavors of Ubuntu, such as Kubuntu, run apt-get install kubuntu-desktop (or edubuntu-desktop, xubuntu-desktop, or xubuntu-desktop).

If the GUI is more your style, the *desktop packages can be installed using Adept, Synaptic, or another package manager.

I'm curious.  If I decide to go with the Kubuntu desktop and don't like it, can I change back to Gnome?  would I use a similar command?  Will changing back really mess things up?

---

### Post by youthforlinux on 2007-01-24
use:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

if you want to install KDE

and if u dont like it use:

```
sudo aptitude remove kubuntu-desktop
```

If you have any more questions two good links to look at are:

[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

and

[http://www.psychocats.net/ubuntu/kdegnome]("http://www.psychocats.net/ubuntu/kdegnome")

and don't worry you won't mess up ubuntu!!!!

---

### Post by 23meg on 2007-01-24
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Use aptitude when installing and you can easily reverse it if you don't like KDE.

Note that kubuntu-desktop includes everything Kubuntu has, beside the KDE desktop environment. If you just want KDE itself, install the *kde-core* package.

---

### Post by mojoman on 2007-01-24
When you have more than one desktop (say Gnome and KDE) or windowmanager (say Fluxbox or WM) installed your login manager (with Ubuntu that's GDE, the login screen you see) will let you chose which one to log into. You can chose which on to set to default.

You can remove installed packages with apt-get remove. Read up on man apt-get, it's a bit but well worth the effort. You can install, remove, purge the system from config files etc etc. Aptitude is a similar tool, I don't have very much experience with it but I think it's better at removing unused dependencies (though I think it requires that the application was installed using aptitude rather than apt-get).

The downside is that when you install something (say KDE on Ubuntu) you might install a lot of stuff as dependencies (i.e. all the packages that KDE depends on) that isn't necessarily removed with apt-get remove. One option is to install a program to weed out unused dependencies, such as deborphan. 

Personally, I always have a look at what will happen before I do it. Use apt-cache search and apt-cache show to find out more about a certain package. Also, you can do apt-get install -s with any package, -s meaning simulate and this shows what will be installed (including dependencies). You can then have a look at their size etc with apt-cache show.

Hope this helps.
/Mojoman

---

### Post by xael on 2007-01-24
georgetoon,

The reason we encourage you to use "aptitude" is  because "apt-get" has problems with some dependencies (these are programs needed to run other programs, but when the original programs are removed, the dependencies are left in the hard disk) and these problems do not occur when aptitude is used.

---

