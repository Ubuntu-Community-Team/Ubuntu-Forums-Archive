---
title: "help! many problem!"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by asusrules on 2006-04-25
whenever i install an app, i get this meesage at the end of the installation, i dont understand what is it saying, should i be worried about it? "you should use apt-get update to fix these errors"

also, i get no sound when i play mp3 in Rhythmbox music player, how can i fix that?

thanks

---

### Post by Nikusan on 2006-04-25
[QUOTE=asusrules]whenever i install an app, i get this meesage at the end of the installation, i dont understand what is it saying, should i be worried about it? "you should use apt-get update to fix these errors"

also, i get no sound when i play mp3 in Rhythmbox music player, how can i fix that?

thanks[/QUOTE]

The apt-get error is probably related to one of the repositories either being down or you not having a key installed for it. Neither of those is a really serious problem but if you want to, post the content of you /etc/apt/sources.list file and we'll have a look.

Re the mp3 playback, do you have mp3 support installed? If not you can find instructions here: [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Sef on 2006-04-25
Have you tried using it from the terminal?  Applications > Accessories > Terminal

sudo apt-get update

See if that takes care of your problem.

---

### Post by asusrules on 2006-04-26
the sound still doesnt work. help please

also, if i download a .gz or .bz2 from ff, how can i install them?

---

### Post by Sef on 2006-04-26
> also, if i download a .gz or .bz2 from ff, how can i install them?

First, install build-essential.

sudo apt-get install build-essential

then click on the link below.

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

Note: with bz2 the j needs to replace the z in -xvzf

> whenever i install an app, i get this meesage at the end of the installation, i dont understand what is it saying, should i be worried about it? "you should use apt-get update to fix these errors"

Go into Synaptic and check at the bottom.   See if any packages are broken.   If there are then click on 'Edit' and then highligh 'Fix Broken Packages.

---

