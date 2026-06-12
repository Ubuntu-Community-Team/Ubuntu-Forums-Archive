---
title: "Am I the only one who prefers Clearlooks to Ambiance?"
date: 2010-04-03
forum: Art &amp; Design
---

### Post by PryGuy on 2010-04-03
Hi all!
In fact I don't like the Lucid's Ambiance theme at all! I even made my own Clearlooks based theme that I called 'ClearLucid'. It has purple window titlebar instead of blue.

```
#!/bin/bash

mkdir -p ~/.themes/ClearLucid
echo -e "[Desktop Entry]\nName=ClearLucid\nType=X-GNOME-Metatheme\n\n[X-GNOME-Metatheme]\nGtkTheme=Clearlooks\nMetacityTheme=Clearlooks\nIconTheme=ubuntu-mono-light\nGtkColorScheme=fg_color:#000000000000,bg_color:#ededececebeb,text_color:#1a1a1a1a1a1a,base_color:#ffffffffffff,selected_fg_color:#ffffffffffff,selected_bg_color:#9740600b99e1,tooltip_fg_color:#000000000000,tooltip_bg_color:#f5f5f5f5b5b5" > ~/.themes/ClearLucid/index.theme

exit 0
```

---

### Post by rogerpittman on 2010-04-03
I actually like Ambience myself...the only real issue I've had with Lucid (albeit a minor one) is the placement of the window buttons on the left instead of the right. Other than that, I've been very pleased with it.

---

### Post by PryGuy on 2010-04-03
Well, I move them to the right with the following command:
```
gconftool-2 -s /apps/metacity/general/button_layout -t string 'menu:minimize,maximize,close'
```

---

### Post by Psumi on 2010-04-04
Am I the only one who prefers Openbox to a DE?

---

### Post by NightwishFan on 2010-04-04
I like most GTK themes. Pretty much anything that does not have a lot of messy rendering glitches is fine with me. Clearlooks is one of my favorites along with Nodoka.

As for DE vs WM, use what works for you. I see as much excellence and aesthetics in something minimal as I do in the glassy widgets of KDE. I prefer a full blown environment though.

---

### Post by daasdingo on 2010-04-04
Well, I use openbox and gnome-settings-daemon to get the gtk theme and other settings like network proxy etc.

But I really DONT like the new ubuntu theme; its pink and has window buttons on the left, thats just horrible! Besides, what connects pink to ubuntu? I understood brown-orange stuff but pink?

One good thing is that the new upper taskbar looks great!

---

### Post by Psumi on 2010-04-04
> **daasdingo said:**
> Well, I use openbox and gnome-settings-daemon to get the gtk theme and other settings like network proxy etc.

Icons CAN be changed via gtkrc.mine, use the FOLDER NAME OF THE ICONSET, NOT THE NAME SPECIFIED IN INDEX.THEME.

Network proxy is for paranoia victims.

---

### Post by rudihawk on 2010-04-05
I like clearlooks more than ambiance too!

---

### Post by PryGuy on 2010-04-06
Well, if we want a 'heavy' theme, [Equinox]("http://gnome-look.org/content/show.php/Equinox+Ubuntu+Packages?content=121882") looks far more professional and polished compared to the Ambiance. They could take it and replace the Vista like window controls with round buttons or something. Do the guys from Canonical know what professional design is?

---

### Post by BeRA on 2010-04-08
I used Clearlooks until yesterday... and then I installed Ambiance (I'm using karmic)... and it's orange instead of pink... perfect (pink is not really my favourite colour)... I find Ambiance to be just the right blend of simplicity, good looks and usability (my preference of window controls placement excluded)... shortly= quite original (and recognisable), and perfect choice for a default theme... my new favourite :KS

---

### Post by parn on 2010-04-09
The Ambiance is sadly... lousy and the displacement of the window buttons complete its lousiness - yes yes it is easy to move it back to its **rightful** place but still...

The default background of Ambiance looks like the bastardize child of a Mac OSX + Window Vista stock wallpaper (_if you are unfortunate enough to have a copy of Vista, check Windows\Web\Wallpaper\img25.jpg_).

---

### Post by shuttleworthwannabe on 2010-04-13
Check [this ]("http://arstechnica.com/open-source/news/2010/03/pretty-penguin-five-great-themes-for-the-gnome-desktop.ars")page out--look at the Elementary theme. cool, huh!

---

