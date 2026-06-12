---
title: "Enlightenment Package problem"
date: 2006-04-06
forum: Bug Reports / Support
---

### Post by El_Matthews on 2006-04-06
Hello All

I just installed Ubuntu to try it out and indeed the installation whent smoother as with debian, after installation of the base system I installed enlightenment (my favorite desktop manager). This installed and updated GDM corectly.

Now I log on to enlightenment and I don't have the programs under the left mouse button. it seems that this is not create correctly. Under user menus I have Gnome and the only program created is Console\Python interpreter. Where is all the rest like networking / interenet etc (mozilla)

Segond point : when I install debian with enlightenment the standard theme is different and has smoother menus. If you want I can copy it and sent it to your support.

---

### Post by localzuk on 2006-04-06
Have you tried using the 'Regenerate Menus' link under one of the other menus?

---

### Post by El_Matthews on 2006-04-06
[QUOTE=localzuk]Have you tried using the 'Regenerate Menus' link under one of the other menus?[/QUOTE]


Yes I tried but this didn't help. In debian there is also the command update-menus but this doesn't seem to exists here

---

### Post by localzuk on 2006-04-06
You could hand create the menus via their config files for the time being...

---

### Post by El_Matthews on 2006-04-06
yes I could handle it via the config files but the reason I am trying Ubuntu is that they say it is easier to manage than Debian. Until now I am not convinced :( 

Of course to launch my programs I can open a command prompt and launch it but I am installing a window manager to do that for me. Yes I know, I am a little bit lazy at that point.

---

### Post by localzuk on 2006-04-06
Ubuntu is in the 'Universe' repository so is not actually a supported package by Ubuntu. It is provided for people who want it but won't actively be worked on by the developers. There are currently a few different 'flavours' (ie. Window Managers and their associated apps) being supported, such as Ubuntu (gnome), Kubuntu (KDE) and xubuntu (XFCE).

The packages for enlightenment are likely to be of a similar level of usefulness to those on debian as they are not likely worked on that much more than those at debian.

Also, I always thought that one of the reasons to use Enlightenment was the fact that it could be hacked at in config files in order to make it run exactly as you wish.

---

### Post by El_Matthews on 2006-04-11
If I am correct, you are telling me that Ubuntu delivers me a package (enlightenment) but that the deloppers won't work or support their own package ? 

This is more an answer I am used to receive from Microsoft that from a Linux community.

If the package is provided it should work correctly and be supported!

And yes, on this point you are right, enlightenment is a high configurable window manager. BUT I don't see the added value of having to create an entry in the config files every time I install/uninstall a program. Configuring themes etc is somthing else.

---

### Post by KrustybRuffle on 2006-04-13
The vesion of Enlightenment that Debian uses is 16.7, while Ubuntu is using 16.6, hence the difference in default theme. You can download the debs from Debian & install them without problems if you want to.

As for the menus, try: ```
sudo apt-get install menu
``` It's the Debian package that has update-menus, then after you run that regenerate E's menus in the maintenance section.

It seems to have worked for me.

---

### Post by El_Matthews on 2006-04-13
Hello KrustybRuffle


Think you, I installed the package menu and now it works fine. I also added the debian testing repository to my sources.list and installed enlightenement from there.

Now everything seems to be fine. 

Thanks

This thread can be closed

---

### Post by KrustybRuffle on 2006-04-16
For future reference, you can just download the .debs from [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=enlightenment&searchon=names&subword=1&version=stable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=enlightenment&searchon=names&subword=1&version=stable&release=all)

put them all in one folder & run ```
sudo dpkg -i enlightenment*.deb
```
These are from the stable branch of Debian, & this is probably safer/easier than changing your sources.list....

Sorry I didn't mention that before, but I was really tired when I made the above post & just didn't think of it...

also:

the enlightenment & enlightenment-data packages are required, but the themes are optional, though you probably knew that I thought I should mention it for the next time someone is trying to figure this out & reads this thread :)

---

