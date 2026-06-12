---
title: "What version should I of installed?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Prodigy1 on 2007-12-30
Well here is my problem,  I installed the "Ubuntu 6.06 LTS - Supported to 2011" version. problem is I come from a Windows world and have no clue about the Linux command system but like the features of the server edition as it does what I was looking for. My problem lies with the lack of a GUI. Is there a version that has this or how can i get a GUI in this. My apologies if this is old hat.

Thanks in advance for all replies.

---

### Post by taurus on 2007-12-30
You just install Gnome window manager and you would have a GUI.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by JoshuaRL on 2007-12-30
Yeah, everything except the Server editions have a GUI.

Ubuntu is run off of the Gnome desktop.  [http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

Kubuntu is run off of the KDE desktop.  [http://en.wikipedia.org/wiki/Kde](http://en.wikipedia.org/wiki/Kde)

Xubuntu is run off of the XFCE desktop.  [http://en.wikipedia.org/wiki/Xfce](http://en.wikipedia.org/wiki/Xfce)

All are based of of Debian Linux [http://en.wikipedia.org/wiki/Debian](http://en.wikipedia.org/wiki/Debian)

LTS stands for Long Term Support.  It is the most stable edition currently out and is most likely to work with everything else.

You can install KDE or XFCE with

```

sudo apt-get update
sudo apt-get install kubuntu-desktop

```

or

```

sudo apt-get update
sudo apt-get install xubuntu-desktop

```

---

### Post by jken146 on 2007-12-30
> **JoshuaRL said:**
> 
LTS stands for Long Term Support.  It is the most stable edition currently out and is most likely to work with everything else.


Not most likely to work with new hardware.

---

### Post by PeterJS on 2007-12-30
> **jken146 said:**
> Not most likely to work with new hardware.

And this is why I'm looking forward to Hardy, so I can have my cake and eat it to. I can recommend using the current LTS and feel confident it's going to have the best support and new applications.

---

