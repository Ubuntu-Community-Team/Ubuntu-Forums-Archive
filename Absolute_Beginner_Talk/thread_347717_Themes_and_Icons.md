---
title: "Themes and Icons"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by RDUBBALO on 2007-01-27
Hello I was just wondering if anyone knew how I could get the icons at the bottom like how the Mac  OS has. and also there is other icons and little displays i see in some images Like CPU usage and other things. i cant figure out how to get all that stuff on there. Any ideas.

---

### Post by taurus on 2007-01-27
Themes/Icons:
[http://www.gnome-look.org](http://www.gnome-look.org)

The display things could be gDesklets, adesklets, gkrellm, etc.

---

### Post by RDUBBALO on 2007-01-27
ok I dont know what to pick here and does this go for Ubuntu Im not sure what to pick i see alot of themes.

---

### Post by ComplexNumber on 2007-01-27
good(IMO) mac OS X themes  are OSX and gnome-apple. they can be fouind at the link that tauarus has provided.

>  Like CPU usage and other thingsfurther to what taurus has said, you could always use the system monitor. right click on your panel, select 'add to panel', then select system monitor. by default, the system monitor will display the cpu activity, but you can also add the following (see first screenshot. the second screenshot shows the cpu activity, RAM usage, network usage, and cpu temperature, respectively. the cpu temperature is an applet called gnome sensors applet)

---

### Post by taurus on 2007-01-27
> **RDUBBALO said:**
> ok I dont know what to pick here and does this go for Ubuntu Im not sure what to pick i see alot of themes.

[http://www.gnome-look.org/content/show.php?content=13548](http://www.gnome-look.org/content/show.php?content=13548)
[http://www.gnome-look.org/content/show.php?content=31618](http://www.gnome-look.org/content/show.php?content=31618)

---

### Post by RDUBBALO on 2007-01-27
does this work for ubuntu edgy i dont know how to install this after i DL it.

---

### Post by ComplexNumber on 2007-01-27
> **RDUBBALO said:**
> does this work for ubuntu edgy i dont know how to install this after i DL it.
yes, i have them installed on mine. 

if you have more than one user on your system, you can install them systemwide so that everyone can use them. to do so, highlight the package. right click on it and select 'extract here'. then fire up the termial and cd to the directory where you have extracted it. then type sudo cp -R <package name> /usr/share/themes to install a theme, and type sudo cp -R <package name> /usr/share/icons for icon themes.

to install it in your home directory (if there is just you using the PC), then extract the tarball, as above. then put the icons in /home/<your-username>/.icons. put the themes in /home/<your-username>/.themes.

---

