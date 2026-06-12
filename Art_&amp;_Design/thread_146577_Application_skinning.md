---
title: "Application skinning?"
date: 2006-03-18
forum: Art &amp; Design
---

### Post by lzfy on 2006-03-18
Hi, i would like to know if it is possible to skin gnome apps, if so how? I did this on Windows and it's very easy to do with a reshacker, is it similar in Linux?

---

### Post by IYY on 2006-03-18
You mean downloading new themes for Gnome? That's very easy. Just go to System > Preferences > Themes and select the one you want. If you want to install new themes / icons, you can get them at

[www.gnome-look.org](www.gnome-look.org)
or
[art.gnome.org](art.gnome.org)

Unless you mean manually setting the skin of each application?

---

### Post by lzfy on 2006-03-18
> Unless you mean manually setting the skin of each application?

yes that's what I mean, kind of hacking the app, replacing bitmaps.

---

### Post by bvc on 2006-03-18
I'm no developer but from what I've see you could do that by modifying the source code, but that's major overkill and would be permanent til you mod and compile the source again. Other than that, no.

---

### Post by Kimm on 2006-03-19
no need to hack the app. GTK+ (default widget system in GNOME), is skinable from the beginning. The theme used by Ubuntu by default is "Human", I'm using "Clearlooks Cairo - Human" which is somewhat similar, but more modern.
The theme usualy contains bitmaps for all types of buttons and filetypes.

You can make your own themes, I dont know how but if you study existing themes I'm sure you can figure it out.

PS.
Xubuntu (XFCE4) also uses GTK and can use the same themes
Kubuntu (KDE) uses Qt, which is also themable.

---

### Post by engla on 2006-03-19
If you want to use different skins for different apps, you can write a starter script that does something like this:
```
GTK2_RC_FILES=~/.themes/Olive/gtk-2.0/gtkrc gedit
```
This is for the theme Olive, starting gedit. It only changes the gtk theme though, so the window borders still look the same..

---

### Post by lzfy on 2006-03-19
Thanks for the reply's :) I'm actually creating my own theme and I want to change some stuff per application. For example I want to make round buttons for rhytmbox (play, next etc...) but only for that app and not for other apps.

---

### Post by bvc on 2006-03-19
cool....too bad that doesn't work from the ~/.gtkrc-2.0

---

