---
title: "Custom Boot, Login Screens"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Het Irv on 2008-01-31
One thing that I miss from Windows is a program that I could use to change the way my boot and login screens looked.  The program even had a tool in which you could make your own boot screens.  While I am not expecting it to be as easy in Ubuntu I was wondering if any one has tried and if they have what worked?

I am going to make a VM on my computer so that I can mess with anything without doing damage to anything important.

---

### Post by steve-shinn on 2008-01-31
You can download, install and even modify login screens from :-
[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by jan quark on 2008-01-31
menu > system >administration > login window

---

### Post by billgoldberg on 2008-01-31
Sure, the login-screen is called gdm.

Those can be found on [http://www.gnome-look.org](http://www.gnome-look.org)

direct link:
[http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=150](http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=150)

Installing a login-screen is as easy as going to "system -> administration -> login window". Going to the second (or third tab) and draggin it (the .tar.gz, i think) in there.

Modifying the login (keeping the layout, but changing the picture) is easy. You untar the folder, remove the picture and insert the new one (make sure it has the same name and size, use the gimp to modify it). And the re-tar it.

Costum grub themes can be found here:
[http://www.gnome-look.org/content/search.php](http://www.gnome-look.org/content/search.php) (search for "grub")

(i'm not sure how to install them)

---

### Post by Blutack on 2008-01-31
The bit that shows the screen whilst loading is called Usplash, and making themes for it is not the easiest thing in the world.  However, there are plenty you can download and install.
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)
Once loaded, the login screen is handling by GDM.  I wrote a quick'n'dirty script to change the login background to your wallpaper, as well as shift the elements round to make it look a bit nicer (to me, anyway).  If you grab that you should see how easy it is to modify GDM themes.
[http://ubuntuforums.org/showthread.php?t=667382](http://ubuntuforums.org/showthread.php?t=667382)
Both GDM and Usplash themes can also be found premade on sites like [www.gnome-look.org](www.gnome-look.org).

---

