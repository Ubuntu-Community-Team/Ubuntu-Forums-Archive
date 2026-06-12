---
title: "Getting Classic Themes"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Penguin002 on 2007-04-23
Hello,

I am a newbie to Ubuntu and I just recently installed 7.04. However when I go to change my theme I do not see the classical themes there like Ocean Dream. At work when I use Ubuntu they have all the themes pre-installed, however when I installed I only have 3: human, crux, and some other one. How can I get all the classical ones back? 7.04 should support them.

Any help is greatly appreciated.

---

### Post by bwhite82 on 2007-04-23
Try installing the package, "gnome-themes-extras".

EDIT: "Ocean Dream" is in the package, "gnome-themes"

---

### Post by Penguin002 on 2007-04-23
Thanks for the advice, but ummm how do I go about installing that??

---

### Post by bwhite82 on 2007-04-23
From a console:
> sudo apt-get install gnome-themes gnome-themes-extras

---

### Post by Ganda_Melga on 2007-04-23
Hum...are there any themes for XFCE? I can't find any on my Xubuntu. And the system almost have no system sounds.

Will the themes consume much resources and processor power?

---

### Post by bwhite82 on 2007-04-23
> sudo apt-get install xfwm4-themes xfce4-goodies

Try these, they shouldn't consume too much resources, only way to find out is try, you can always remove the packages:

> sudo apt-get remove xfwm4-themes xfce4-goodies

---

