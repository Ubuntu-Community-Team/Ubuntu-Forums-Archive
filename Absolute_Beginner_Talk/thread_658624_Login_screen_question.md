---
title: "Login screen question"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by EnergySamus on 2008-01-04
Hello!
I do like the avalible choices for the login screen, but is there a way to make a picture that you like become the login screen? 

EnergySamus

---

### Post by SOULRiDER on 2008-01-04
Got o [http://gnome-look.org](http://gnome-look.org) and downlaod some GDM themes if thats what you mean.

---

### Post by PeterJS on 2008-01-04
There's a bunch over at gnome-look.org see if there's something you like there. If you're dead set on making your own here's the documentation on how:
[http://live.gnome.org/GnomeArt/Tutorials/GdmThemes](http://live.gnome.org/GnomeArt/Tutorials/GdmThemes)

---

### Post by rcsarver on 2008-01-04
I dont know how to make your own, but there are some themes available at [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by markusf21 on 2008-01-04
Go to [[COLOR="Blue"]_Gnome Look_[/COLOR]]("http://gnome-look.org/")
 Go to GDM Themes on the left. You can pick one from there. 
If you want to make your own picture get one with a lay-out you like, save it to your desktop and extract it. 
Then put your picture in but rename it to the one that was in there. 
Then re compress it. 
To use it go to system/ admin/ log in window click the local tab and hit add. 
Go to the compressed file and install then click it from the list. It will probably still show the old pic. Log out to check that it worked.
There very well may be an easier way but this is the one I know

---

### Post by EnergySamus on 2008-01-06
Ok I found a theme that I like... But how do I install it? It is a Mac OS X theme that is sweet!

Thanks
EnergySamus

---

### Post by EnergySamus on 2008-01-06
Oh.. And just to say: It says that it is a GTK 2.x Theme... I don't have a clue what that means!!!:lolflag:

---

### Post by PeterJS on 2008-01-07
GTK 2 themes are for widgets like buttons and scroll bars after you log in. Linux theming is broken in to 4 components:
Login (GDM or KDM)
Window Borders (Metacity or KWIN)**
Window contents aka widgets (GTK or QT)
Icons

*The first element in parenthesis is the Gnome component and the second is the matching KDE component

**Or Emerald for both if running compiz

Each of which can be theme'd independently, usually people chose themes for each element that fit together to form a coherent whole, but that's not required.

System > Perferences > Appearance is where the GTK theme is set, under the customize button there's a tab to set the window borders and icons. Themes are installed in ~/.themes and icons are in ~/.icons.

GDM themes are set and installed through System > Administration > Login Window.

---

