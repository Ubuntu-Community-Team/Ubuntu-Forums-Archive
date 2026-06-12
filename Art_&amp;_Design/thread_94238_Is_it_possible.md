---
title: "Is it possible?"
date: 2005-11-23
forum: Art &amp; Design
---

### Post by Minyaliel on 2005-11-23
Since nobody on IRC had an answer....

This is how my theme looks: (hosted on my own account)

[IMG]http://i25.photobucket.com/albums/c72/Minyaliel/newbg211105.png[/IMG]

[IMG]http://i25.photobucket.com/albums/c72/Minyaliel/nyttemaogsa.png[/IMG]

One thing that's been bugging me: my gnome panel's grey. GREY! I want it to be black to fit the rest of the theme. Anyone know how to tweak it?

---

### Post by AlexMartinius on 2005-11-23
Right click the panel, properties. You can set the color to black there.

Edit: that really doesn't look very good. Some things in the panel don't change color. I knew that would be too easy. :)

---

### Post by Minyaliel on 2005-11-23
[QUOTE=AlexMartinius]Right click the panel, properties. You can set the color to black there.

Edit: that really doesn't look very good. Some things in the panel don't change color. I knew that would be too easy. :)[/QUOTE]
eew lol that looks horrible :P (btw, would be nice to change the grey bottom panel aswell if it's possible...)

---

### Post by Minyaliel on 2005-11-23
I've played around with it.... with some transparency it looks alright... weee...! Well, thanks ;)

[IMG]http://i25.photobucket.com/albums/c72/Minyaliel/newtwist231105.png[/IMG]

---

### Post by bvc on 2005-11-24
```
style "clearlooks-panel"
{
  bg[NORMAL] = "#000000"
}
class "*Panel*" style "clearlooks-panel"
widget_class "*Panel*GtkToggleButton" style "clearlooks-panel"
widget_class "*Panel*GtkButton" style "clearlooks-panel"
```
you'll have to add and change font's etc....as well, but you would at least have more control.

---

