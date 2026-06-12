---
title: "My Canon EOS 400D need a Photo Album storage"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Johnson on 2007-08-08
Can you tell me what is the best program to store photos with? Photo Album program, righty. :(

I would love to get loads of suggestion with + and - with the program, thanks.

---

### Post by Kobalt on 2007-08-08
I use [digiKam]("http://www.digikam.org"), since I'm a KDE user, and I really love it. 
Import from my Canon IXUS 500 works like a charm. It lets you manage your albums easily (and not like F-Spot that creates a whole bunch of directories with dates and other stuff). You can view your pictures from thumbnails preview to diaporama just as easily, you can edit your pictures (size, format, color, brightness, red eye...). It also supports sync with iPods and distant galleries over the internet.

---

### Post by Johnson on 2007-08-08
> **Kobalt said:**
> I use [digiKam]("http://www.digikam.org"), since I'm a KDE user, and I really love it. 
Import from my Canon IXUS 500 works like a charm. It lets you manage your albums easily (and not like F-Spot that creates a whole bunch of directories with dates and other stuff). You can view your pictures from thumbnails preview to diaporama just as easily, you can edit your pictures (size, format, color, brightness, red eye...). It also supports sync with iPods and distant galleries over the internet.

Does it work good in Gnome also?
How do I update it in Gnome?

---

### Post by Kobalt on 2007-08-08
Yes, you can install it with ```
sudo apt-get install digikam
```
But it will install the KDE libraries though.

---

### Post by Obor on 2007-08-08
Another vote for **digikam**. I use gnome and I've tried a lot of photo management application and digikam is the best IMO. I use a lot of KDE programs, don't have any problems with it.

Another things to try would be 
f-spot which is default in ubuntu(I don't like the way it organizes photos)
[picasa]("http://picasa.google.com/linux/"), my choice in windows but as it runs using wine, the linux version has some quirks.
[GQview]("http://gqview.sourceforge.net/"), less features but you might like it.
[imgSeek]("http://imgseek.net/"), I haven't tied this one

---

### Post by Johnson on 2007-08-08
I used the Add/Remove program option and I got now 0.9.1 digiKam, how can I upgrade it to 0.9.2 without messing around to much? :(

---

### Post by Obor on 2007-08-08
> **Johnson said:**
> I used the Add/Remove program option and I got now 0.9.1 digiKam, how can I upgrade it to 0.9.2 without messing around to much? :(

I'm using 0.9.1 as I don't see a reason for upgrade but if you really want to

You can add the kubuntu feisty repo from [http://www.digikam.org/?q=download/binary/](http://www.digikam.org/?q=download/binary/)
(do it by editing sources list or using "add software sources" in the menu)
and run
```
sudo apt-get update && sudo apt-get upgrade
```

---

