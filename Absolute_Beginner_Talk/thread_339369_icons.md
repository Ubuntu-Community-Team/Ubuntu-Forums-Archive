---
title: "icons"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Daniel9389 on 2007-01-15
hi i downloaded a set of icon off [www.gnomelook.org](www.gnomelook.org) and i don't know how to install them PLEASE help me

---

### Post by NeoLithium on 2007-01-15
Go to SETTINGS -> PREFERENCES -> THEMES, click on Theme Details, and you can either drag & drop into the window, or click the install button :)

---

### Post by aysiu on 2007-01-15
Go to System > Preferences > Themes and then drag and drop the .tar.gz file to the theme manager window.

---

### Post by ComplexNumber on 2007-01-15
> **aysiu said:**
> Go to System > Preferences > Themes and then drag and drop the .tar.gz file to the theme manager window.
thats not the best option. that will bring up an error if a tarball contains more than 1 icon theme such as [this]("http://gnome-look.org/content/show.php?content=46010") one.



> **Daniel9389 said:**
> hi i downloaded a set of icon off [www.gnomelook.org]("http://www.gnomelook.org") and i don't know how to install them PLEASE help me
select the  package that you downladed, right click on it and select 'extract here'. then place them in /home/<your-username>/.icons. this will make the icons available only to you. to make them available for everyone (assuming that there are more than 1 user on your PC), place them in /usr/share/icons instead.

---

### Post by ardchoille42 on 2007-01-15
> **ComplexNumber said:**
> thats not the best option. that will bring up an error if a tarball contains more than 1 icon theme such as [this]("http://gnome-look.org/content/show.php?content=46010") one.


Yes, I agree, the theme manager isn't very good at installing multi-theme tarballs like the icons package you linked. This is why I always recommend that users copy the theme to either ~/.themes or /usr/share/themes. I submitted a bug about this to the gnome project a while back but they haven't fixed the theme manager yet.

---

### Post by CameronCalver on 2007-01-17
Yes sometimes inside the .tar.gz there is High Res Low Res etc

---

### Post by Daniel9389 on 2007-01-17
yea it said the file format is invalid when i did it though

---

### Post by Akillese on 2007-10-20
_SOZ every 1 this is a test i couldnt get the underline to work lol:popcorn::lolflag::guitar::lolflag::lolflag::lolflag::lolflag::popcorn:_

---

