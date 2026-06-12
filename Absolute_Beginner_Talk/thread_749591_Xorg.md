---
title: "Xorg?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by CraigW on 2008-04-08
I'm having troubles resizing all my fonts after the installation of the Nvidia Drivers, 
they are all way too big, I had fixed it before by adding "DisplaySize     577 360" in my Xorg thing, but it didnt work this time, my question is has anyone found a solid fix? and also how do I open that Xorg configure screen, its blue and you have to keep clicking next and it runs through configuring just about everything.....

---

### Post by mikeyphi on 2008-04-08
I think the code you're looking for is:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by mali2297 on 2008-04-08
> **CraigW said:**
> 
they are all way too big, I had fixed it before by adding "DisplaySize     577 360" in my Xorg thing, but it didnt work this time, my question is has anyone found a solid fix? 

You can try adding the following line in the "Device" section:
```

        Option   "DDC"  "No"

```

> 
and also how do I open that Xorg configure screen, its blue and you have to keep clicking next and it runs through configuring just about everything.....

```

sudo dpkg-reconfigure xserver-xorg

```
Note that this will rewrite xorg.conf.

---

### Post by Therion on 2008-04-08
If that's NOT it (above) you probably want:```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by GreenB on 2008-04-08
hey, i am quite a newbie, but i'll try to give a hand anyhow.
if you mean the /etc/X11/xorg.conf file when you talk bout the ' Xorg Thing' i belive you should be able to resize the font's by adding something like 
```

DisplaySize some_size some_other_size

```
after the "Section Monitor", maybe more like 140 than 537 

and the by the way the
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
should be run if you want the file to update automatically after you have made changes to the xorg.conf - probaly not a bad idea

---

