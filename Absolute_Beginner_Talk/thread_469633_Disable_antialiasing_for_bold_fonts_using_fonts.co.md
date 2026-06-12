---
title: "Disable antialiasing for bold fonts using fonts.conf"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Cardy on 2007-06-10
I use following construction to Disable antialiasing for bold fonts im my ~.fonts.conf to avoid superbold (shadow) effect.

<match target="font">
 <test name="weight" compare="more"><const>medium</const></test>
 <edit mode="assign" name="antialias"><bool>false</bool></edit>
</match>

It works fine for some application (Firefox, Thunderbird), but it does not work for other (gnome terminal, ). Why so?

---

### Post by Cardy on 2007-06-10
Small PS: gnome terminal is only one application ignoring my ~/.fonts.conf. Font is Lucida Console or any.

---

### Post by packjamNL on 2007-06-18
There is a macintosh font wich realy looks good in ubuntu, and is called Myriad Pro.otf (Adobe). It's the font thats on their iPods and websites.
Try to find it somewhere, buying is expensive.
I think I renamed it to .ttf but not sure anymore try both.

---

