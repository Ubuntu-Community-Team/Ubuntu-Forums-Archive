---
title: "Vista transformation pack for ubuntu"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by aachen on 2008-04-07
I have  downloaded on  vista transformation pack from the following website.

[http://www.gnome-look.org/content/show.php/Vista+Transformation+Pack+for+GNOME?content=63106](http://www.gnome-look.org/content/show.php/Vista+Transformation+Pack+for+GNOME?content=63106)

I extracted the tarball and there are different folders for icons, apps, emblems, panel etc. with .png files.
But I dont have any idea how to install this pack. Can anyone explain step by step how to install. I am absolutely new to this. Instructions from above link are tough to understand.

---

### Post by NightwishFan on 2008-04-07
I believe you can skin the panel by dragging the image onto the panel itself.

---

### Post by SunnyRabbiera on 2008-04-07
eh that pack really isnt that good.
there are other ways to make your system vista like.
but tell me are you doing this for familiarity or just to trick your buddies and family to think you are using vista?

---

### Post by aachen on 2008-04-07
I am just doing it to trick people..what are other good ways to do it? Vista sucks big time in terms of performance but the graphics is nice.

---

### Post by NightwishFan on 2008-04-07
Get a wallpaper, emerald and gtk-theme. It should be pretty close if you just use one panel at the bottom. :)

I know there are people that make exact clones somehow but I was never interested much. I normally use a Mac-like/Kde hybrid.

---

### Post by aachen on 2008-04-07
I dont know how to install emerald and then how to install these themes ? :(

---

### Post by NightwishFan on 2008-04-07
To install emerald make sure you can first run at least normal effects with compiz. Then run this command.
```
sudo apt-get update && sudo apt-get install emerald
```
I believe you can then press alt+f2 and type:
```
emerald --replace
```
To install themes just download the beryl themes on gnome-look.org they should be of a .emerald extention then just install them via the emerald manager.

---

### Post by tbrminsanity on 2008-04-07
> **aachen said:**
> I am just doing it to trick people..what are other good ways to do it? Vista sucks big time in terms of performance but the graphics is nice.

I just forced my family to switch over.  My wife was really pissed off at the start but now can't go back to windows.

---

### Post by SunnyRabbiera on 2008-04-07
well there a few cool things you can use to make Ubuntu vista like.

First there is emerald, its in the repositories. There are several themes for it that are vista like on Gnome look, the themes under compiz or beryl are normally emerald themes.
then there is this aero theme on gnome look, out of all of them I like this one the best:
[aero clone]("http://www.gnome-look.org/content/show.php/Aero-clone?content=57352")
for a windows like menu check out the mint repositories here:
[http://www.linuxmint.com/repository/]("http://www.linuxmint.com/repository/")
and look for the mint menu, mint is based on ubuntu so its packages are compatible so you should have little issues.
your end result might not be perfect but it it will look pretty neat.

---

### Post by aachen on 2008-04-07
I downloaded emerald themes. but I also want to change the icons..I downloaded vista inspirate from this link:
[http://www.gnome-look.org/content/show.php?content=28352&forumpage=6](http://www.gnome-look.org/content/show.php?content=28352&forumpage=6)

but again no idea how to install it. Its written nowhere about installation procedure.

---

### Post by bilal.17 on 2008-04-07
to install icons extract the tar ball with the icons and move the folder to ~/.icons  then go to appearance and select the gtk-theme you are using, then click on customize, from there click on the icons tab and select your icon theme from there

---

### Post by erginemr on 2008-04-07
This is how my desktop looks like:
[http://ubuntuforums.org/showpost.php?p=4406694&postcount=2](http://ubuntuforums.org/showpost.php?p=4406694&postcount=2)

You can also decorate your grub boot screen and gdm login screen:
[http://ubuntuforums.org/showpost.php?p=4406738&postcount=4](http://ubuntuforums.org/showpost.php?p=4406738&postcount=4)
(Disclaimer: Decorating the boot screen is dangerous. So, don't do it without an extensive reading on how to install and configure gfxboot first)

If you are interested, you can follow these steps to install them:
[http://ubuntuforums.org/showthread.php?t=664387&highlight=theme](http://ubuntuforums.org/showthread.php?t=664387&highlight=theme)

For a more detailed explanation on how to install themes in Gnome:
[http://maketecheasier.com/how-to-redesign-your-desktop-the-wow-way/2008/01/10](http://maketecheasier.com/how-to-redesign-your-desktop-the-wow-way/2008/01/10)
[http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/)

---

