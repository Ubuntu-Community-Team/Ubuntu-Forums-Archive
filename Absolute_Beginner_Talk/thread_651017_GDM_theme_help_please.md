---
title: "GDM theme help please"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2007-12-27
hello,

I have two GDM themes that i downloaded that are not installed right. I did the usual, i went to the login manager and drug the .tar.gz there and pressed the install button, nothing showed up. I did it again and it said that it was already installed. still not on the list of login screens, I looked in the file and it seems like everything is there. I really want these login screens, is there anyhting else i can do?

thanks in advance!!

---

### Post by deepank on 2007-12-27
Just a guess .... I think the installation of the theme must have happened and ur theme changed from default to custom.

---

### Post by spiderbatdad on 2007-12-27
can you go to /usr/share/gdm/themes/whatever and show me a screenshot of the contents of "whatever?" If you don't want to do that, I can tell you the greeter has to be named GDMGreeterTheme.desktop  (as far as i know) and if you could, show the contents of that file as well.

---

### Post by NilsE on 2007-12-27
I have never had luck with the auto installer for GDM themes.  

I just extract the theme to the  folder:

/usr/share/gdm/themes  

Make sure you have the theme folder open in Nautilus then open the archive and extract to the themes folder with the recreate folders and overwrite files selected.

Oh yeah, make sure you are in Nautilus with root permissions.  In a terminal type

gksudo nautilus

Then go into system > administration > Login window > local tab then select it.

---

### Post by rockinlinux on 2007-12-28
well i changed the GdmGreeterTheme,desktop file. The encoding was something strage so i editied it to UTF-8 and everything works good, well it shows up in the list now but i have not tried to reboot yet....

thanks for the help guys :)

---

