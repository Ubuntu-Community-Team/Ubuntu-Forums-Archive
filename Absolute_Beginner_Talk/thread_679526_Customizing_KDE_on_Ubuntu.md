---
title: "Customizing KDE on Ubuntu"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by z|x on 2008-01-27
There is this whole customization guide at [http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/) but its for GNOME. Could someone help me customizing KDE in the same way?

I'm looking forward to getting the Dark Ubuntu Theme working.

Thanks

---

### Post by swoll1980 on 2008-01-27
kde-look.org just open your control panel go to the themes and drop the respective tar files in there place for example down load icon set open icons in the control panel hit install an address bar will pop up just drag your icon tar file into address bar and hit enter

---

### Post by z|x on 2008-01-27
Ok, but what the Emerald theme? How do I get emerald to work on KDE? And the same for GTK and GDM.

Thanks

---

### Post by z|x on 2008-01-27
bump??

---

### Post by sunexplodes on 2008-02-04
KDE apps don't use GTK, they use QT. There is a panel in KControl that allows you to define what GTK theme your GTK applications use. 

As far as GDM goes, it doesn't play very nicely with KDE, in my experience (nor does KDM play nice with GNOME). Best way to go is "dpkg-reconfigure kdm" in terminal. That will allow you to choose KDM as the default. If you want to switch back and forth, CTRL+ALT+F1, then type "sudo killall gdm" followed by "sudo kdm", or vice-versa. 

To get compiz/emerald working, type "compiz --replace" in the terminal.

---

