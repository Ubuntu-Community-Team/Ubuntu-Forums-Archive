---
title: "What is GTK, Compiz, Beryl ect. and how do i install the themes"
date: 2006-11-19
forum: Art &amp; Design
---

### Post by Jamesbowden on 2006-11-19
I a quite new to Ubuntu I have been messing around with the themes on Ubuntu a lot recently. i have downloaded themes and icons form websites like Gnome-look and Gnome-art.

however i keep coming across things call GTK themes, Compiz, and Beryl.

As far as i can tell this is a method of installing themes on the Gnome desktop.

could someone please explain to me what these are, and how to use them.


thanks

---

### Post by smartalecks on 2006-11-19
**GTK** is the base library that the GNOME environment runs on. It is what is installed with Ubuntu, as GNOME is the environment that Ubuntu uses. **Beryl and Compiz** are composite managers, and are what create special effects such as a desktop cube. They are extra and are not installed by default. **GTK Themes** are themes written using GTK, and are usually used by composite managers such as Beryl or Compiz. If you are looking for regular themes that Ubuntu can use without extra stuff such as Beryl and Compiz, you are looking for **Metacity themes** (assuming you are using GNOME). You can find them here: 

[http://gnome-look.org/index.php?xcontentmode=101](http://gnome-look.org/index.php?xcontentmode=101)

To install the Metacity themes, download the theme from the above url, then go to System > Preferences > Themes, and install by following the instructions. It's pretty easy from there :D.

---

### Post by camilluk on 2006-11-19
I think I read somewhere that Beryl and ATI graphics cards are not compatible. I'm not sure what it is and what it does, but I think it's because ATI drivers don't allow 'composite'. Two questions:
1. I have an ATI X600 card and the proprietary ATI drivers installed on AMD-64bit. Is my system compatible with Beryl?

2. I can't see Beryl listed in Synaptic. How can I get it?

---

### Post by smartalecks on 2006-11-19
ATI cards can be used with Beryl/Compiz. Installing Beryl isn't that easy, however, and [COLOR="Red"]you can kill your machine[/COLOR], if you aren't careful. 
You can't see it in Synaptic because you do not have the repository added yet.

**To install Beryl on a machine that has an ATI card, see these:**

[INDENT]You said you already have the drivers installed, but here's the HOWTO anyway:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/GCDrivers](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/GCDrivers)

Install Beryl with AIGLX (what Edgy ships with, instead of XGL):
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

I recommend following the HOWTOs that are hosted on beryl-project.org, but if none of those work and you have a clean install, look here:
[http://ubuntuforums.org/showthread.php?t=290841](http://ubuntuforums.org/showthread.php?t=290841)[/INDENT]

---

### Post by Jeff250 on 2006-11-19
Metacity is Ubuntu's window manager, and it is in charge of displaying the window border, which is usually a few pixels wide on the left, right, and bottom, and also includes the title bar up at the top, including the minimize, etc. buttons.  A metacity theme will change the look of this window border.

GTK2 is a widget toolkit that is responsible for widgets inside of the window like the scrollbar, checkboxes, drop-down menus, buttons, and the like.  So choosing a new GTK2 theme will change the look inside of the window border.

It gets a little bit more complicated with compiz and beryl.  Compiz and beryl are also window managers like metacity, so if you use them, they are also responsible for drawing the window border.  compiz supports metacity themes, so this is how you can theme the window border with compiz.  I'm not up to date with beryl, but I believe that it recently supports metacity themes now too, in addition to their own type of theme, which I'm not very familiar with.

---

### Post by camilluk on 2006-11-20
> Installing Beryl isn't that easy, however, and [COLOR=Red]you can kill your machine[/COLOR], if you aren't careful

gee... I'm really scared now!!! Not sure that I'll try if that's the case. Is there anything in particular I need to pay attention to???

---

### Post by Jamesbowden on 2006-11-20
So how would i go about installing a GTK 1.x/2.X theme?

---

### Post by smartalecks on 2006-11-20
> **camilluk said:**
> gee... I'm really scared now!!! Not sure that I'll try if that's the case. Is there anything in particular I need to pay attention to???

Backup your xorg.conf, gdm file, and any others that you make changes to. If you applying it to your main machine you might want to print out the instructions as well. Also, being comfortable with the terminal is generally a good thing.

"Kill" your machine might be a bit much, but it can mess up Xorg and crash it (meaning that you will not have a GUI to work with when you boot up, just a terminal).

---

