---
title: "Ubuntu's Default GUI"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Grahamb on 2006-04-03
What is Ubuntu's Default GUI?

How easy is it to change ?

thanks

---

### Post by Madpilot on 2006-04-03
Ubuntu's default GUI is Gnome, which is very easy to theme & tweak.

It's also fairly easy to install KDE, XFCE, or another desktop if you want.

---

### Post by Grahamb on 2006-04-03
Great thanks for the Quick reply

---

### Post by Nordoelum on 2006-04-03
[quote=Grahamb]What is Ubuntu's Default GUI?
 
How easy is it to change ?
 
thanks[/quote]
Ubuntu = GNOME
Kubuntu = KDE
Xubuntu = XFCE
 
Got the picture :P

---

### Post by meborc on 2006-04-03
to install other desktops:

kubuntu:
**sudo apt-get install kubuntu-desktop**

xubuntu:
**sudo apt-get install xubuntu-desktop**

but be warned that strange things will happen in your gnome menu :mrgreen: you will have kde-apps as well as gnome apps... but there are ways to 'workaround' it and they are listed somewhere here in this forum...

to switch between different desktops, chose session from your login screen

---

### Post by jrib on 2006-04-03
I'd just like to suggest that when you install things (especially meta-packages), you should use aptitude

As meborc, said to get/try kubuntu and xubuntu:

```
sudo aptitude install kubuntu-desktop
```
```
sudo aptitude install xubuntu-desktop
```

The advantage to using aptitude over apt-get is that it will keep track of the dependencies that get installed.  So when you try to remove something like kubuntu-desktop using aptitude, all of the unneccessary dependencies will be removed as well.  However, with apt-get, an 'apt-get remove kubuntu-desktop' will only remove the metapackage and leave all the dependences installed.

---

