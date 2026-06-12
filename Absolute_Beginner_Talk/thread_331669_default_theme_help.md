---
title: "default theme help"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-04
haha i'm so dumb

ok I was messing around and I dragged a mouse cursor theme to the system themes and pushed apply and now ubuntu won't even load my desktop or panels or anything.  I'm on xp right now.


How do you change the theme to default through command line.  (I have beryl installed though.)
I can access the command line though the recovery mode.

Can I just remove the gnome-theme-manager somehow?

Thanks.

---

### Post by MkfIbK7a on 2007-01-04
do you know the exact name of the theme if so you can try (not sure if this will work)

sudo rm <name/and/path/of/theme/>

---

### Post by MkfIbK7a on 2007-01-04
sorry this will just remove the mouse theme im not sure if gnome will revert to the default theme...

---

### Post by zmuth734 on 2007-01-04
> **wert613 said:**
> do you know the exact name of the theme if so you can try (not sure if this will work)

sudo rm <name/and/path/of/theme/>

where is path of the themes if you install themes by dragging them to the themes manager

---

### Post by MkfIbK7a on 2007-01-04
sorry do know:redface:

---

### Post by zmuth734 on 2007-01-04
they go to /home/yourname/.themes after u drag them to that theme manager

I didn't see the mouse cursor theme there, it is only in /.icons where it is supposed to be

maybe if I reinstall the gnome theme manager through the command line

how do I do that? ](*,)

---

### Post by MkfIbK7a on 2007-01-04
i doubt that reinstalling gnome theme manager would help but do this

cd /home/yourname/.themes
ls

paste the output here

---

### Post by zmuth734 on 2007-01-04
> **wert613 said:**
> i doubt that reinstalling gnome theme manager would help but do this

cd /home/yourname/.themes
ls

paste the output here

Ok I will in a couple mins if this doesn't work (I found this with google)

Metacity themes should be installed in ~/.themes/[themename].

If you are using GNOME 2.0.x, the only way to change themes is by changing the /apps/metacity/general/theme gconf key with gconf-editor or gconftool-2 to the name of the theme you want to use. For example:

gconftool-2 --type=string --set ~/.themes/[themename] [themename]


I don't really know how to do that though?


EDIT:  I think I might have to switch the GTK theme instead of the metacity theme b/c i think metacity themes are for the windows and gtk is for the panels etc.

I want to try GTK theme switch but I don't know how to install it from command line.  I'm not sure if its in the respositories.

[http://freshmeat.net/projects/gtkthemeswitch/](http://freshmeat.net/projects/gtkthemeswitch/)

---

### Post by zmuth734 on 2007-01-05
I just want to let everyone know that I resolved it by running the fail-safe gnome session at login,
i went to system>preferences>theme and removed the mouse cursor icons (you're not supposed to install mouse cursor icons there) under theme details > icons.  It made the mouse cursors into icons for my ubuntu and it was going crazy.  Thanks everyone!!!  I'm so happy I didn't have to reinstall.

---

### Post by MkfIbK7a on 2007-01-05
> it made the mouse cursors into icons for my ubuntu and it was going crazy.
lol

glad you solved it yourself you just have to put your mind to it

---

