---
title: "Unthemed elements on ubuntu 14.04"
date: 2014-11-06
forum: Art &amp; Design
---

### Post by mc-rpg on 2014-11-06
Good morning everyone,

I recently upgraded to ubuntu 14.04 and I have found that my favorite theme (MediterraneanLight of the MediterraneanNight series) doesn't look very good on it. I have been able to fix most of the stuff that didn't show up right but there are a few left that I really don't know how to fix. See screenshots below:

[IMG]http://i.imgur.com/TXZgYHw.jpg[/IMG]

[IMG]http://i.imgur.com/S65U5Lb.jpg[/IMG]

It seems that those GTK elements (highlighted with the red arrow) aren't being taken into account by the theme but I have no way of knowing which are those. If there is any gtk theme maven here that could help me I would really appreciate it.

---

### Post by Frogs Hair on 2014-11-06
I've seen this with a number of 3rd party dark themes and I would make sure the GTK version is compatible which is 3.10 on 14.04. You can also report the bug to the theme creator and I see a new related comment on Gnome Look that could be yours . This is a problem that needs to be addressed on the theme provider end.

---

### Post by mc-rpg on 2014-11-06
Yes I know and I reported it to the creator. I post here in order to see if I can find the name of that gtk element to patch the theme myself in the meantime.

---

### Post by mc-rpg on 2014-11-06
For whatever it's worth I found the element. Commenting this:

GtkOrientable {
    background-color: @theme_bg_color;
} 

from the gtk-widgets.css file fixed that issue.

---

