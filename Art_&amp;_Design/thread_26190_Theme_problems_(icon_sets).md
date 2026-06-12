---
title: "Theme problems (icon sets)"
date: 2005-04-12
forum: Art &amp; Design
---

### Post by fubz on 2005-04-12
For the life of me I cannot get icon sets to work under gnome 2.10 on Hoary!  I want the d3a to work but it just sticks to plain default gmome icons, same thing happens with the GNAT and any other icon set i download from gnome-look.org or art.gnome.org! Please if anyone know's hwo to solve this please tell me.  Here is a screenshot of my problem [http://shell.mics.co.za/~michael/Screenshot.png](http://shell.mics.co.za/~michael/Screenshot.png)

---

### Post by erkki70 on 2005-04-12
Hi,
Could you precise how you're installing the icon themes step by step and if you get any messages?
Do you have a  ```
.icons
```folder in your  ```
/home/your user name/
```?

Cheers,
Erkki

---

### Post by fubz on 2005-04-12
I have tried 2 ways:

1) extract icon sets to ~/.icons
2) using the theme-manager to install the .tar.gz

None seem to work!

---

### Post by erkki70 on 2005-04-12
Hi,
Have you tried login out and in again?
Sometimes it helps...

Cheers,
Erkki

---

### Post by fubz on 2005-04-12
yes I have tried that.

---

### Post by Slapdash on 2005-04-12
make sure its not in a dbl folder in .icons.   example iconX/iconthemeX

Are you using the same login as what you install it with?

---

### Post by fubz on 2005-04-12
no there are no double folders!

michael@rizon:~$ du --max-depth=2 -h .icons/
819K    .icons/gnant/16x16
827K    .icons/gnant/24x24
827K    .icons/gnant/32x32
1.4M    .icons/gnant/48x48
1.5M    .icons/gnant/64x64
5.3M    .icons/gnant
4.0K    .icons/gnome/LowContrast
4.0K    .icons/gnome/48x48
4.0K    .icons/gnome/HighContrast
4.0K    .icons/gnome/HighContrastInverse
16K     .icons/gnome
3.9M    .icons/gartoon/scalable
3.9M    .icons/gartoon
9.2M    .icons/
michael@rizon:~$

---

### Post by Slapdash on 2005-04-12
hmmm... looks fine to me.

mine is slapdash/.icons/icontsetname   as wel.

and you are sure there is a index.theme file in there with them?

P.S I'm asking all this because I cant view your screenshot at all.

---

