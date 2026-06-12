---
title: "Custom logon screens?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2007-04-02
I'm running Xubuntu, is there an easy way to use custom log on screens? And if there is, where's a good place to find new ones?

---

### Post by crispy_420 on 2007-04-02
I am familar with how to in gnome and it should be similar in xfce too. Gnome uses a program listed in the menu as "Login Window". From here you will many options like: auto login, remote login, etc. But the part you will need is the first tab, local login. By the way you will need root password to access it too.

For themes, try these links:

[http://www.gnome-look.org/](http://www.gnome-look.org/)

[http://www.xfce-look.org/](http://www.xfce-look.org/)

[http://www.kde-look.org/](http://www.kde-look.org/)

---

### Post by aysiu on 2007-04-02
Gnome and XFCE both use GDM in Ubuntu/Xubuntu

Go to [http://www.gnome-look.org](http://www.gnome-look.org) and download any GDM theme (not to be confused with GTK themes). Do not extract the theme file or do anything to it. Just leave it on your desktop.

Then press Alt-F2 and type ```
gksudo gdmsetup
``` Go to Themes part and install a new theme. Find the file you had previously downloaded and select it. To make it active, make sure the little circle next to the newly installed theme is filled in (a black circle instead of an empty circle).

---

### Post by Majin Zero on 2007-04-02
Thanks guys.

---

### Post by Majin Zero on 2007-04-02
darn, ok, I downloaded the logon screen I want, a gdm one, ran the gdmsetup thing, installed from the .tar.gz file, but it doesn't show up in the choices, only the default ones.

just incase it helps it's this one:

[http://www.gnome-look.org/content/show.php/SystemAccess?content=52145](http://www.gnome-look.org/content/show.php/SystemAccess?content=52145)

---

### Post by aysiu on 2007-04-02
That's weird. It shows up... but not as *SystemAccess.*

For me, it shows up as *AGlanceIsEnough*.

Looks as if it's badly constructed theme.

---

### Post by Majin Zero on 2007-04-02
thanks again, you're right.

---

