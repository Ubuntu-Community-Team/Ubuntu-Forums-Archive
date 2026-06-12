---
title: "[SOLVED] Help trying to remove..."
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by apauloisdead on 2007-10-12
I'm trying my best to customize my whole desktop environment, but i really am i pretty big n00b with linux. The good thing is struggling to learn how to change these things is really getting me to learn a few things all around.

...but anyways, i'm going for a real simple look. I finally figured how to get this nova theme installed, but there's a few things i'd like to change. For one, i'm trying to get rid of all of these icons, like the ones in the window list, and the ones in the menu.

Also there is a gradient on certain things in certain windows i'd like to just make plain white.


I circled all the things in the picture i attached.


Any suggestions?

---

### Post by apauloisdead on 2007-10-12
Whoops, didn't realize the attachment didn't upload.

...file was too big, i just cut the pic in half.

---

### Post by apauloisdead on 2007-10-13
...??? ...anybody?

---

### Post by jbaerbock on 2007-10-13
I wouldn't know what to tell ya. From what I can see you would either have to change all the icons manually by right clicking>properties or learn how to edit theme files.

---

### Post by Stall on 2007-10-13
Those are just icon themes. Download them from somehwere. Install new them (the exact same way tou install a theme), and use them with your theme by going to system - preferences - theme - customize - icons, and select the icon themes you just downloaded.

Try [www.gnome-look.org](www.gnome-look.org) to get new icon themes.

Hope this covered it.

---

### Post by bodhi.zazen on 2007-10-13
I suggest you take a look at Fluxbox or Openbox. They are alternate desktops but both are clean, fast, and efficient.

---

### Post by jbaerbock on 2007-10-13
> **bodhi.zazen said:**
> I suggest you take a look at Fluxbox or Openbox. They are alternate desktops but both are clean, fast, and efficient.

Yeah thats not gonna be very good for a newbie. Gnome and KDE and maybe xfce are for newcomers.

---

### Post by urukrama on 2007-10-13
You can easily remove the icons from buttons, etc, but you'll have to edit your theme file. Go to /home/USERNAME/.themes/NAME OF YOUR THEME/gtk-2.0 and open the gtkrc file. Then either edit or add the following at the beginning of the document:

> gtk-button-images = 0 #disabled icons on buttons
gtk-icon-sizes = "panel-menu=16,16" #size of icons in the panel-menu

If you replace the 0 by 1 you will have icons on buttons. The second line allows you to change the icon sizes on panel menus.

In Xfce (a different desktop environment), you can choose not to have icons in the menus (Right click on menu button > Properties > Show Icons in Menu). I don't think there is such an option in gnome.

What you could do, however, is use Alacarte, the menu editor, to remove the icons manually for each entry. In case the icon is replaced by a default one if you remove it, replace it with an empty png file/icon.

To run alacarte, type Alt+F2, type alacarte and press enter. If it isn't installed, tick the alacarte box in Synaptic and install it.

---

### Post by apauloisdead on 2007-10-15
Thanks guys, i ended up trying out xubuntu, and i really like it. I think it fits what i'm looking for really good.

---

