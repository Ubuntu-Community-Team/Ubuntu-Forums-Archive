---
title: "themes in XUBUNTU"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-06-16
can someone tell me how i can install a new theme in xfce

---

### Post by Beej on 2006-06-16
I think if you have to decompress the file to your .themes folder in your home directory.

tar -xvzf theme.bz2 /home/username/.themes

from the terminal

if -xvzf doesn't work try -xjvf i can't remember which one is correct.

I can't remember if there is a tool to select different gtk themes preloded, there definately is for window decorations.  If you cant find one through the apps menu you can install this one from synaptic.

sudo apt-get install gtk-switch

then run switch2 from terminal to change gtk2 theme or switch1 to change GTK1 theme. 

I'm at work at the mo but I'll try and check these instructions are correct when I get home.

Regards,

Ben.

---

### Post by dolby on 2006-07-25
```
sudo cp theme /usr/share/themes
cd /usr/share/themes 
sudo tar -xvzf (or jxvf) theme
```

---

### Post by videodrome on 2006-07-26
Are we talking about icon themes here? Because those do not work right at all. 

There's all kinds of strange undocumented voodoo going on there. I spent 2 days messing with the icons, trying, for example, to get all of the control panel icons and all of the menu icons themed. 

Some inhererit some of the high color icons; some want to seemingly be in the pixmaps dir, while others think they live in the icons/48x48 realm. Still others, like the mixer taskbar icon, exist in the buggy mysterious netherworld somewhere. Currently my mixer icon is a cup filled with pens and pencils. 

And don't even get me started on trying to edit the actual menus themselves. I'll scream if I have to edit one more .desktop file.

---

