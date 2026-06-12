---
title: "Add new fonts in Ubuntu 7.10"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by lupas on 2007-11-19
How to add fonts for this version. Take into consideration that i'm a newbie in linux. Just a week :)

---

### Post by stido on 2007-11-19
click:

System ->
Preferences ->
Appearance ->
Fonts ->
Details... ->
Go To Fonts Folder ->

drag and drop font files you want installed to that recently opened Nautilus window

---

### Post by SunnyRabbiera on 2007-11-19
one of these days they got to make a better font installer for gnome, the one in KDE kicks the crap out of what gnome has

---

### Post by lupas on 2007-11-19
I have done that but in the office prog. there seem to be missing or can not be used . Why?Scroll down to change font type does not appear the new fonts that i have add to .

---

### Post by stido on 2007-11-19
> **SunnyRabbiera said:**
> one of these days they got to make a better font installer for gnome, the one in KDE kicks the crap out of what gnome has

yuuuppp! \\:D/

---

### Post by stido on 2007-11-19
> **lupas said:**
> I have done that but in the office prog. there seem to be missing or can not be used . Why?Scroll down to change font type does not appear the new fonts that i have add to .

have tried restarting your office app after installing the fonts?

is it TrueType fonts (.ttf) you wanna use? if it is then it should work and be available.
 
other cause: maybe your fonts must be system-wide available in order for your app to see it. if that's the case, then you might want to install it directly to fonts:///

from terminal:
```
sudo nautilus
```

go to location:
```
fonts:///
```

drag and drop the fonts there

---

### Post by lupas on 2007-11-19
ok thanks

---

### Post by stchman on 2007-11-19
> **lupas said:**
> How to add fonts for this version. Take into consideration that i'm a newbie in linux. Just a week :)

Here is how to install fonts in Ubuntu.

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

The /usr/share/fonts folder is owned by root so you need root privileges to install fonts system wide.

Also when fonts are copied the command

```
fc-cache -f -v
```

needs to be used.

---

