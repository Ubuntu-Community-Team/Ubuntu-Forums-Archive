---
title: "System Wide Theming."
date: 2006-05-26
forum: Art &amp; Design
---

### Post by daneness on 2006-05-26
This may be a tough to solve issue, but anyways: I'm trying to write a script that installs a theme (icon, interface elements, backgroung and GDM) and I want to make the theme the default for all new users. I haven't been able to find the files I need to edit to make this happen. I'm doing this to install Ubuntu as an OEM operating system without using the nasty brown theme. Oh, and just to let you know the theme files I'm using are Relaxing GDM, nuoveXT icons, VistaBut for the windows and toolbar, and a background featuring the company's logo.

---

### Post by ComplexNumber on 2006-05-26
what was your question again? are you asking what directories to install the themes in so that they can be accessed systemwide? if so:
-gtk theme - /usr/share/theme
-metacity theme - /usr/share/theme
-icons theme - /usr/share/icons
-gdm - /usr/share/gdm.
-wallpaper - /usr/share/backgrounds

---

### Post by aysiu on 2006-05-26
One place to look would be /etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/interface/%gconf.xml, which has the line: ```
<local_schema locale="C" short_desc="Gtk+ Theme">
<default type="string">
<stringvalue>Human</stringvalue>
</default>
<longdesc>Basename of the default theme used by gtk+.</longdesc>
``` If you want to poke around a bit yourself, try ```
grep -i -n -r human /
```

---

### Post by daneness on 2006-05-28
Thank you both. That's exactly what I needed to make it all work. Now time to finish writing the script! :)

---

### Post by PingunZ on 2006-05-28
You mean a .sh script, I was thinking of making one too could you post it ? 
Or post the howto you used to make a .sh script ...
Btw that GDM looks great ;)

Grtz PingunZ

---

