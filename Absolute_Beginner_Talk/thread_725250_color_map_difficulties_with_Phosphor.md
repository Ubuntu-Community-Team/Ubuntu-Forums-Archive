---
title: "color map difficulties with Phosphor"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by D351 on 2008-03-15
I'm not sure if this should go somewhere between beginner talk, development, and art & design but here goes...

So, I'm trying to get the Phosphor screensaver to appear exactly as it already does, except in purple. I dug through the info I could find and found out how to install a colormap in the code, but I've come across a problem. Even after figuring out how to install allegro, I'm having no success in even experimenting with it because I can't seem to save the results of running "colormap" in a format that phosphor will recognize... I'm using "-install '/location/location/filename' and just can't seem to get it to react at all. I'm thinking that I just need to figure out what file type to save it as...

---

### Post by ashikase on 2008-05-22
According to the xscreensaver man page, "-install" is a boolean option that is used to enable/disable creation of a private colormap to prevent problems when running on low-color displays; it is not used to specify your own set of colors.

To use your own colors, you can define the following values in your ~/.Xresources file (if it does not exist, create it):

```

Phosphor.background:      Black
Phosphor.foreground:      Green
Phosphor*fadeForeground:  DarkGreen
Phosphor*flareForeground: White

```

The color values shown above are the defaults. The color names are defined in /etc/X11/rgb.txt.

---

### Post by D351 on 2008-05-22
Much much thanks... Minor question. Do you mean /X11/Xresources/x11-common or /X11/Xsession.d/30x11-common_xresources?

---

### Post by ashikase on 2008-05-22
"~" (tilde) is an alias to your home directory (i.e. /home/d351)

Therefore, you should edit (or create) the file "/home/d351/.Xresources".

The .Xresources file should be loaded automatically when you start X. However, if it appears that it is not, you may need to create a start-up item that executes the following command:
```
xrdb ~/.Xresources
```

---

### Post by D351 on 2008-05-22
Awesome... This works exactly as I'd hoped... Right now I've got:

Phosphor.background:      Black
Phosphor.foreground:      magenta3
Phosphor*fadeForeground:  DarkMagenta
Phosphor*flareForeground: White

Still playing around with it though... :)

---

