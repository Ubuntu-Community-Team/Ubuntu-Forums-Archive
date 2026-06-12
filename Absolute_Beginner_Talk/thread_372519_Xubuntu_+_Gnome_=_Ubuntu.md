---
title: "Xubuntu + Gnome = Ubuntu?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Jevid on 2007-02-28
I have been running Xubuntu on my old laptop for about a week and thanks to many of the posts I've read here, it's working very well. I booted up with the Ubuntu live CD, specifically to check out Gnome. I really liked it. So, in Xfce, I went into Synaptic Package manager, and checked "Gnome Desktop Environment" to install. I didn't proceed with it because it appeared that it was going to possibly remove some Xfce related files when installing Gnome. 

Two questions: if I do just install Gnome into Xubuntu, I can choose which interface to load, Xfce or Gnome, when I boot up, correct?

Also, if you have Xubuntu, and you load Gnome on top of it, is that exactly the same as Ubuntu itself, or will there be other differences?

If it's better, I'll just wipe out the hard drive and do a clean install of Ubuntu. My basic understanding is that the underlying system is the same. Xfce and Gnome are just the GUIs, so it shouldn't be necessary to do anything other than install Gnome

Thanks - Jevid

---

### Post by taurus on 2007-02-28
1.  Yes, you have an option to choose which window manager you want to use at the GUI login screen, Options at the bottom left.

2.  Yes, it should be the same as if you were installing Ubuntu (Gnome).
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Motoxrdude on 2007-02-28
You can install ubuntu in xubuntu. 
```
sudo apt-get install ubuntu-desktop
```
When that completes, at your login screen select "Gnome" under sessions.

---

### Post by rsambuca on 2007-02-28
In this case it is definitely better if you use aptitude rather than apt-get.

---

### Post by Jevid on 2007-02-28
Thanks very much for the feedback. I'll go ahead and use aptitude to install Gnome tonight. On a related note, do most experienced Linux users just use apt-get and aptitude instead of Synaptic Package Manager? Any good guidelines on when to use one over the other? 

Thanks - Jevid

---

### Post by Songwind on 2007-02-28
aptitude or apt-get are a lot more efficient if you know precisely what you want.  If you aren't sure of the package names, the search features of Synaptic or KPackage are very useful.  I'm not a guru or anything but I have found that using both works well.

---

### Post by kittyhawk63 on 2007-02-28
How are you Feisty Fawn test users finding the new version?

---

