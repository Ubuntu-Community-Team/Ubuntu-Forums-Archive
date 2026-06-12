---
title: "Locate where are installed icons"
date: 2005-07-01
forum: Art &amp; Design
---

### Post by frodon on 2005-07-01
Hi

I've installed some new gnome icon themes like MMX-Mercury-L (from GNOME-look.org) and I want to affect these icons to custom desktop shortcuts. Does someone can tell me where are installed the icons of the theme (MMX-Mercury-L icon theme for exemple), I search in /usr/share/pixmaps/ but I didn't find them.

thanks

---

### Post by WakkiTabakki on 2005-07-01
[QUOTE=frodon]Hi

I've installed some new gnome icon themes like MMX-Mercury-L (from GNOME-look.org) and I want to affect these icons to custom desktop shortcuts. Does someone can tell me where are installed the icons of the theme (MMX-Mercury-L icon theme for exemple), I search in /usr/share/pixmaps/ but I didn't find them.

thanks[/QUOTE]

Try ~/.themes or ~/.icons 

/N

---

### Post by PMO6022 on 2005-07-01
You can always try the "locate command", after you update the database. In a console, try:
**sudo updatedb**
**locate <name of file>**

---

### Post by frodon on 2005-07-01
[QUOTE=PMO6022]You can always try the "locate command", after you update the database. In a console, try:
**sudo updatedb**
**locate <name of file>**[/QUOTE]

Yes i try it but without find what i'm looking for ... or my eyes are really bad   ... maybe it's that  :-) 

thanks

---

### Post by bvc on 2005-07-01
Directories with a '.' are hidden
.themes
.icons
in your home directory
to see them, open nautilus and go to View>Show Hidden Files
Go to Edit>Preferences>Views tab to make it default behavior.

---

### Post by frodon on 2005-07-01
[QUOTE=bvc]Directories with a '.' are hidden
.themes
.icons
in your home directory
to see them, open nautilus and go to View>Show Hidden Files
Go to Edit>Preferences>Views tab to make it default behavior.[/QUOTE]

ls -a also do it.

I don't know why but I didn't think to search in home directory hidden files  :roll:  
I know that very often software are installed here .... where is my head !

thanks all, I have the icon power in my hands now  :smile:

---

