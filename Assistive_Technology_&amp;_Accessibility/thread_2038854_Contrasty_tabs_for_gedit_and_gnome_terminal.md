---
title: "Contrasty tabs for gedit and gnome terminal"
date: 2012-08-07
forum: Assistive Technology &amp; Accessibility
---

### Post by vasa1 on 2012-08-07
By default, the active and inactive tabs in gnome terminal and gedit aren't very different when one uses the Ambiance theme.

I posted a workaround a while ago here at the time of 11.10:

[http://askubuntu.com/questions/46182/gnome-terminal-tabs-are-very-dark-difficult-to-tell-which-tab-is-in-use/73779#73779](http://askubuntu.com/questions/46182/gnome-terminal-tabs-are-very-dark-difficult-to-tell-which-tab-is-in-use/73779#73779)

It still works for 12.04. In short, after backing up the file, edit **/usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css** and in the section titled "**.notebook tab**", replace
```

background-image: -gtk-gradient (linear, left top, left bottom,
                                 from (shade (@bg_color, 0.97)),
                                 color-stop (0.80, shade (@bg_color, 0.95)),
                                 to (shade (@bg_color, 0.92)));
```
with

```
background-color: #222222
``` or whatever you like. Alternatively, just tweak the shade values in the existing code.

Please note that I'm using a laptop (Dell Inspiron 1545) and I don't know whether this will work on desktops or other devices.

Edit: this works with [this Greybird theme]("http://ubuntuforums.org/showpost.php?p=12153244&postcount=2") (Xfce) installed on 12.04 as well. There, I just change **.notebook tab** and not **.notebook tab:active**.

---

### Post by vasa1 on 2012-10-04
It appears that tabs in the xfce4-terminal in Xubuntu 12.10 may look like what is reported in this issue: [https://github.com/shimmerproject/Greybird/issues/15](https://github.com/shimmerproject/Greybird/issues/15)

---

