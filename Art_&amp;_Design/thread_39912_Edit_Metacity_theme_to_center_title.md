---
title: "Edit Metacity theme to center title?"
date: 2005-06-07
forum: Art &amp; Design
---

### Post by kaput on 2005-06-07
I really like the [SystemG]("http://art.gnome.org/themes/metacity/778") Metacity theme. However, for some reason, the fact that the window title isn't centered in the theme is driving me nuts. I've tried to contact the author for a bit of advice on how to alter it, but I haven't received a response yet.

Any theming wizards out there willing to give me a hand?

---

### Post by intangible on 2005-06-17
After installing the theme, open the file **~/.themes/SystemG/metacity-1/metacity-theme-1.xml**

You're gonna replace the following two lines:

Line 172:
```
<title color="gtk:fg[SELECTED]" x="3" y="((height - title_height) / 2) `max` 0"/>
``` 
Line 178:
```
<title color="blend/gtk:fg[SELECTED]/gtk:bg[SELECTED]/0.5" x="3" y="((height - title_height) / 2) `max` 0"/>
``` 

With this:
Line 172:
```
<title color="gtk:fg[SELECTED]" x="((width - title_width) / 2) `max` 0" y="((height - title_height) / 2) `max` 0"/>
``` 
Line 178:
```
<title color="blend/gtk:fg[SELECTED]/gtk:bg[SELECTED]/0.5" x="((width - title_width) / 2) `max` 0" y="((height - title_height) / 2) `max` 0"/>
``` 

And that should get you want you want.

---

### Post by kaput on 2005-06-24
[QUOTE=intangible]After installing the theme, open the file **~/.themes/SystemG/metacity-1/metacity-theme-1.xml**

You're gonna replace the following two lines:

Line 172:
```
<title color="gtk:fg[SELECTED]" x="3" y="((height - title_height) / 2) `max` 0"/>
``` 
Line 178:
```
<title color="blend/gtk:fg[SELECTED]/gtk:bg[SELECTED]/0.5" x="3" y="((height - title_height) / 2) `max` 0"/>
``` 

With this:
Line 172:
```
<title color="gtk:fg[SELECTED]" x="((width - title_width) / 2) `max` 0" y="((height - title_height) / 2) `max` 0"/>
``` 
Line 178:
```
<title color="blend/gtk:fg[SELECTED]/gtk:bg[SELECTED]/0.5" x="((width - title_width) / 2) `max` 0" y="((height - title_height) / 2) `max` 0"/>
``` 

And that should get you want you want.[/QUOTE]

Thanks! I'll try it as soon as I get a chance.

---

