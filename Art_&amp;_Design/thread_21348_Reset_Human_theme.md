---
title: "Reset Human theme"
date: 2005-03-21
forum: Art &amp; Design
---

### Post by IdoMcFly on 2005-03-21
I've installed Ubuntu on a box wich had already a home partition so I mounted it as /home

The problem is that is I choose the human theme, it is not the default Human theme (I got blue title bars not brown). How to reset the theme without screwing up my panels configurations ?

---

### Post by dude2425 on 2005-03-21
Check out your ~/.themes folder and make sure there isn't anything in there, also if you've installed Hoary-preview, make sure you have the clearlooks theme engine installed.

---

### Post by bvc on 2005-03-21
I'll take a guess here and say that you have a Human theme in .themes in your home dir that is overwritting with the one in /usr/share/themes. In other words, if you have a Human theme in both .themes and /usr/share/themes the one in you home dir is used first. You can rename it or remove it. Your choice.

---

### Post by IdoMcFly on 2005-03-22
thanks for the answers, I'll try it this evening :)

---

### Post by IdoMcFly on 2005-03-22
~/.themes was not enough.

I've finally screw up my entire .gconf and reinstall ubuntu-artwork.

---

