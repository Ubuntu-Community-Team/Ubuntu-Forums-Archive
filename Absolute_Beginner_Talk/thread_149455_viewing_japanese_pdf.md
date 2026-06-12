---
title: "viewing japanese pdf"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by hezral on 2006-03-23
hi. i have a couple of pdfs that has japanese writings in it but the default pdf viewer doesnt displays the japanese fonts. how can i solve this? i'm using ubuntu breezy fresh install.

thanks in advance

---

### Post by Sutekh on 2006-03-24
- You should look at these packages

[Ubuntu Packages - language-pack-ja](http://packages.ubuntu.com/breezy/translations/language-pack-ja)

[Ubuntu Packages - language-pack-gnome-ja](http://packages.ubuntu.com/breezy/translations/language-pack-gnome-ja)

[Ubuntu Packages - language-support-ja](http://packages.ubuntu.com/breezy/translations/language-support-ja)

 - If these sound like the right thing then you can install them using
```
sudo apt-get install language-pack-ja language-pack-gnome-ja language-support-ja
```
 - Or search for them in Synaptic.  There is also a KDE-pack, if you use KDE (I'm assuming you use GNOME).


 - Then there is this package that is specifically for PDFs

[Ubuntu Packages - xpdf-japanese](http://packages.ubuntu.com/breezy/text/xpdf-japanese)

 - This one is in the multiverse repository so it comes with no support/guarantee

 - You need to enable the extra repositories to get it too.

 - To enable the extra repositories first copy and backup your apt-get sources.list then edit it to enable the multiverse repository
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
 - When the editor opens find *all* the lines which contain **multiverse** like this one and remove the '#'.
```
# deb http://archive.ubuntu.com/ubuntu breezy multiverse
```
 - When they are removed, save the file (Ctrl+O) and exit (Ctrl+X), and refresh the repositories and install it
```
sudo apt-get update
sudo apt-get install xpdf-japanese
```

---

### Post by hezral on 2006-03-24
thanks!

btw aren't these already in the base install for ubuntu?

> You should look at these packages

Ubuntu Packages - language-pack-ja

Ubuntu Packages - language-pack-gnome-ja

Ubuntu Packages - language-support-ja

i'll try xpdf and thanks again!

---

### Post by Sutekh on 2006-03-24
Depends on what kind of base install you did.

If you did a base install using English as the language then the -ja packs aren't installed.  If you did a base install using Japanese, then the -en packs aren't installed.

---

### Post by hezral on 2006-03-24
i see... i think it's installed in mine because i have a japanese keyboard and my japanese docs opens fine in OpenOffice :D thanks!

---

