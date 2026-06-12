---
title: "precise - how to edit top panel ?"
date: 2013-01-22
forum: Art &amp; Design
---

### Post by ThrashManiac on 2013-01-22
Hi, 

I'm using Ubuntu 12.04 LTS with Unity wrapped into the Greybird theme. 

I really want to change the color of the top panel (and, as a result - the color of the font too). I need this color to be different from the default theme color. Is that possible? 

What files and properties I need to add to achieve this?

---

### Post by aldosivi on 2013-02-02
Super + left ALT + right click on panel, then choose Properties from the menu.

---

### Post by Hairy_Palms on 2013-02-03
it will be a css file in the themes folder, for example, the one for ubuntus default ambiance is at 
```
/usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css
```
but the css doesnt always have to be in a seperate file, it could be in the gtk-widgets.css

---

### Post by naano on 2013-02-07
For something like this:
[http://db.tt/lbesS4ju]("http://db.tt/lbesS4ju")

...I use "Tweak Tool" from the Software Center (also known as gnome advanced settings). It works on both Gnome shell and Unity for both 12.04 and 12.10. It's much easier than editing the css manually:mrgreen:. 
If you do want to go the css route, I would suggest using a code editor(like geany) as most of them color code the strings.

---

