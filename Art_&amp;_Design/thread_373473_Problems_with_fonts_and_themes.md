---
title: "Problems with fonts and themes"
date: 2007-03-01
forum: Art &amp; Design
---

### Post by romaluca on 2007-03-01
I have a problem when i launch a program in sudo mode from main meno or run application. In fact the theme and the fonts not show correctly.
I post a screenshot of synaptic opened in sudo mode from "run applicazions" (alt-f2):
screenshot.png

But if i launch synaptic from terminal the theme and fonts are correctly:
terminal.png.

Why???
How i can to do ?
Thanks

---

### Post by mcduck on 2007-03-02
when you run apps with sudo, you are not running them as your own user but as root instead. And every user has their own settings..

But if you want root apps to always have sam theme, icons and fonts you are using there's a easy trick to do that, just run the following commands in a terminal:

```
sudo ln -s /home/<your username>/.themes /root/.themes
sudo ln -s /home/<your username>/.icons /root/.icons
sudo ln -s /home/<your username>/.fonts /root/.fonts
```
These will link your theme directories into root's theme directories.

edit: the difference when you run them from a terminal with 'sudo' is that sudo doesn't correctly load user settings for graphical apps. You should always use 'gksudo for GUI applications, using 'sudo' might cause problems like changing ownership of some of your setting files into root. This would prevent you from logging in to your desktop. So always use 'sudo' for command-line apps and 'gksudo' for GUI apps.

---

### Post by romaluca on 2007-03-02
the gksudo mode return the same result of sudo mode.

the links to themes,fonts icons, exists 


Isn't there another solution?
Thsanks

---

