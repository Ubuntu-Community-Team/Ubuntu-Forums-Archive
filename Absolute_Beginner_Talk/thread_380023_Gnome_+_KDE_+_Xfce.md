---
title: "Gnome + KDE + Xfce"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Contemplator on 2007-03-09
Is it possible to have all the mentioned Desktop Environments installed and available to choose from when logging into a PC (Like Fedora)?
i.e.,

[Login Options]
1 - [Previous Selection]("http://www.gnome-look.org/content/preview.php?preview=2&id=54252&file1=54252-1.png&file2=54252-2.png&file3=&name=Murrina-BluePerl+%28Preview%29")
2 - [Gnome]("http://www.gnome-look.org/content/preview.php?preview=2&id=54252&file1=54252-1.png&file2=54252-2.png&file3=&name=Murrina-BluePerl+%28Preview%29")
3 - [KDE]("http://www.kde-look.org/content/preview.php?preview=3&id=54265&file1=54265-1.jpg&file2=54265-2.jpg&file3=54265-3.jpg&name=DP+Reloaded")
4 - [Xfce]("http://xfce-look.org/content/preview.php?preview=1&id=54248&file1=54248-1.jpg&file2=54248-2.jpg&file3=&name=Cillop+Studio")

<Click on a choice above to see what they look like>

---

### Post by mills on 2007-03-09
i can choose the 1st 3 selections not sure about  xfce

---

### Post by Crooksey on 2007-03-09
Ok...

Xfce is the "xubuntu-desktop" package
KDE is the "kubuntu-desktop" package
Gnome is the "ubuntu-desktop" package

Simply open a terminal and run
```

sudo apt-get update
sudo apt-get install xubuntu-desktop kubuntu-desktop

```

To install XFCE and KDE, then select them from the sessions list in the login window.

---

### Post by Contemplator on 2007-03-09
That would mean I'd have to download 700MB of each, just to get the desktops?

Is there a way to download the desktop files only?

---

### Post by Crooksey on 2007-03-09
```

sudo apt-get install xubuntu-desktop

....

..
Need to get 61.7MB of archives. After unpacking 251MB will be used.
Do you want to continue? [Y/n/?] 

```
<----------------------------------------------------------------------------------------------------------------------------->
```

sudo apt-get install kubuntu-desktop

..

..
0 packages upgraded, 228 newly installed, 0 to remove and 0 not upgraded.
Need to get 211MB of archives. After unpacking 596MB will be used.

```

Thats 300mb total

---

### Post by wxnker on 2007-03-09
KDE/Kubuntu... :D

Do a clean install on a separate partition though. A "clean" kubuntu is way better than a kubuntu full of gnome stuff. At least that's my opinion.

[http://www.ubuntuforums.org/showpost.php?p=2270304&postcount=8](http://www.ubuntuforums.org/showpost.php?p=2270304&postcount=8)

---

### Post by Crooksey on 2007-03-09
Thats just pointless, why install the rest of the system as a dual boot, the desktop package is more than sufficent.

---

### Post by wxnker on 2007-03-09
First of all. It's possible and easy to use the  method's suggested.

>   Thats just pointless, why install the rest of the system as a dual boot, the desktop package is more than sufficent.

The link in my post (#7) kinda shows my opinion but ...I totally disagree.

I absolutely hate the way the kubuntu menu's get crowded with gnome stuff if you don't do separate installs. Well, you have the choice to clean both menus but if you never used kubuntu before it's a bit hard to know what the basic kubuntu menu looks like. 

If you just want a quick peek at kubuntu then a seperate install of coz isn't necessary but if you have the time there are several advantages with a seperate install. 

I believe more users would keep kubuntu along with ubuntu if they actually tried a clean install.

Kubuntu on ubuntu may be a fast and convinient solution, but keeping them appart gives you a better look at both as separate solutions if you want to try which one you like.

When starting out with ubuntu you get a look at the "clean" environment. When you want to try kubuntu you should offer yourself the same. A kubuntu on ubuntu install made me remove kubuntu real quick. A seperate install made me switch from ubuntu to kubuntu. So "pointless" ? Never. :D

**NB** - The previous answer was **NOT** meant to suggest that the "easy way" to run Gnome+KDE+Xfce isn't a good possibility and it was not an answer to question in #1 just a suggestion. I was mainly referring to this thread as a **POLL**, thus stating my opinion: "if you really want to compare gnome and kde. Use clean installs on different partitions".

---

### Post by Contemplator on 2007-03-09
Thanks for that.. I think I'll try out Kubuntu first.. I live in Kenya.. Ordering will be expensive, so I'll have to download (2KB/s)..

I wouldn't mind the clutter.. actually, I'd rather the clutter so that I can feel like I have gained more than I have waited for (downloading).. 

Ubuntu Launch pad suggests  [[Ticket #4094]("https://answers.launchpad.net/ubuntu/+ticket/4094")]:

> Yes, the desktop environments can be installed by installing the relavent meta package from the list below:-

Package - Desktop Environment
ubuntu-desktop - GNOME
kubuntu-desktop - KDE
xubuntu-desktop - Xfce

Where do I get the "Package - Desktop Environment"?

---

### Post by lamalex on 2007-03-09
isn't it free to have it shipped? It was when I got mine shipped? At least it was to USA.

---

### Post by maxamillion on 2007-03-09
1. Xfce
2. Gnome
3. IceWM
4. Fluxbpx or Enlightenment 
5. WindowMaker
6. fvwm
7. Xpde
8. KDE

.... that's roughly my list without much thought put into it. :)

---

