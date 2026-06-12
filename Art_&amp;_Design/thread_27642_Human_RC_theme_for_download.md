---
title: "Human RC theme for download?"
date: 2005-04-17
forum: Art &amp; Design
---

### Post by Spif on 2005-04-17
I was just wondering whether the Human Theme used in the Hoary Release Candidate is available for download. I don't like the new brown-reddish theme... :( 

Here's a screenshot of how it looks: [http://www.1nsp1r3d.co.uk/tmp/gnomebaker/Screenshot.png](http://www.1nsp1r3d.co.uk/tmp/gnomebaker/Screenshot.png)

---

### Post by bvc on 2005-04-17
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/other/HumanOLD.tar.gz](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/other/HumanOLD.tar.gz)
This is my mod of it
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/other/Clearlooks-4Humans.tar.gz](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/other/Clearlooks-4Humans.tar.gz)
screenie
[http://www.kernow-webhosting.com/~bvc/theme/screenshots/clearlooks/Clearlooks-4Humans.jpg](http://www.kernow-webhosting.com/~bvc/theme/screenshots/clearlooks/Clearlooks-4Humans.jpg)

---

### Post by Spif on 2005-04-17
Wow, thanks! :razz:

---

### Post by Spif on 2005-04-17
Synaptic look very odd with HumanOLD installed :-? 

Anybody know where I can get the original Human Clearlooks theme with the square window bordors (check the screenshot)?

---

### Post by klaxnek on 2005-04-17
Here I post two human squared themes (spiff, I believe the first one is what you want):

-------------

Squared Clearlooks Metacity and Human Hoary RC Gtk:
[HumanOld Theme](http://personal.telefonica.terra.es/web/klaxnek/HumanOld.tar.gz)

[IMG]http://personal.telefonica.terra.es/web/klaxnek/HumanOld.png[/IMG] 

--------------

Squared Clearlooks Metacity and Human Hoary Final Gtk with Flat Menus:
[HumanDarkFlat Theme](http://personal.telefonica.terra.es/web/klaxnek/HumanDarkFlat.tar.gz)

[IMG]http://personal.telefonica.terra.es/web/klaxnek/HumanDarkFlat.png[/IMG]

---

### Post by Spif on 2005-04-17
klaxnek, your theme looks weird in Synaptic to :-? Everything else looks normal...

[http://img236.echo.cx/my.php?image=screenshot5ds.png](http://img236.echo.cx/my.php?image=screenshot5ds.png)

---

### Post by bvc on 2005-04-17
[http://www.ubuntuforums.org/showthread.php?t=24903](http://www.ubuntuforums.org/showthread.php?t=24903)

---

### Post by bvc on 2005-04-17
[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/)

---

### Post by bvc on 2005-04-17
according to your screenshot, you want
[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.20.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.20.orig.tar.gz)

uncompress the tarball>open the
ubuntu-artwork-2.20/art/gtk/Human
directory and delete the Makefiles. Make a gtk-2.0 directory and put the gtkrc in it. Make a metacity-1 directory and put the
ubuntu-artwork-2.20/art/gtk/metacity/Human/metacity-theme-1.xml
in it so that you have
Human/gtk-2.0 and metacity-1 dirs.
Rename the Human dir to
Human-2.20 (or anything you want) and put it in .themes

Or, use the tarballs from klaxnek above  :)

---

### Post by Spif on 2005-04-17
[QUOTE=bvc]according to your screenshot, you want
[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.20.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.20.orig.tar.gz)

uncompress the tarball>open the
ubuntu-artwork-2.20/art/gtk/Human
directory and delete the Makefiles. Make a gtk-2.0 directory and put the gtkrc in it. Make a metacity-1 directory and put the
ubuntu-artwork-2.20/art/gtk/metacity/Human/metacity-theme-1.xml
in it so that you have
Human/gtk-2.0 and metacity-1 dirs.
Rename the Human dir to
Human-2.20 (or anything you want) and put it in .themes

Or, use the tarballs from klaxnek above  :)[/QUOTE]

Thank you!

However, I still have the same problem with Synaptic.

---

### Post by bvc on 2005-04-17
synaptic uses root's selected theme.

---

### Post by Spark* on 2005-04-17
The squared version of Clearlooks Metacity from the Hoary RC has a few wrong pixels in the corners, so if you are a pedant like me, you could also use this version instead: 
[http://213.133.111.182/clearlooks/clearlooks-metacity-0.5.2_squared.tar.gz](http://213.133.111.182/clearlooks/clearlooks-metacity-0.5.2_squared.tar.gz)

---

### Post by Spif on 2005-04-23
How do I change the default root theme?

---

