---
title: "How do you coustomize colors in ubuntu/gnome?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Verbatim9 on 2007-01-09
I'm trying to turn both of the "start"/task bars black in gnome, and I'm not having any luck doing so...the only info I've found out is that we're apparently restricted by the themes we have available (i.e. it's apparently not possible to just edit menu colors). The instructions (from [ubuntu eye candy](https://help.ubuntu.com/community/UbuntuEyeCandy#head-112a6ac244086537c549499a0363c6eeac2aaae9) on the wiki) for installing new themes is just to drag them onto the "themes" applet and they'll automatically install themselves...but there's no mention of what constitutes a theme...when i follow the link to [gnome-look.org](gnome-look.org). download a theme, and drag it over the themes applet, it always says "the file format is invalid".

So...is there an easy way to change colors in Ubuntu?
...and if there isn't, what are the requirements for a theme to be able to be installed in ubuntu?

---

### Post by tweedledee on 2007-01-09
> **Verbatim9 said:**
> I'm trying to turn both of the "start"/task bars black in gnome, and I'm not having any luck doing so...the only info I've found out is that we're apparently restricted by the themes we have available (i.e. it's apparently not possible to just edit menu colors). The instructions (from [ubuntu eye candy](https://help.ubuntu.com/community/UbuntuEyeCandy#head-112a6ac244086537c549499a0363c6eeac2aaae9) on the wiki) for installing new themes is just to drag them onto the "themes" applet and they'll automatically install themselves...but there's no mention of what constitutes a theme...when i follow the link to [gnome-look.org](gnome-look.org). download a theme, and drag it over the themes applet, it always says "the file format is invalid".

So...is there an easy way to change colors in Ubuntu?
...and if there isn't, what are the requirements for a theme to be able to be installed in ubuntu?

I've found for the "drag and drop" approach the theme actually needs to be compressed (i.e., don't uncompress it yourself).

Themes themselves are just text files with instructions on what to color how (and a few other things).  If you can't find one you like, you can edit the files in .themes.  Unfortunately, the available guides for themes in gnome aren't very thorough, but you can find some tutorials to get you started, and you can just play around until you find what you want.

---

### Post by jordanmthomas on 2007-01-09
If you are trying to install a theme and it is invalid try this:
**GTK theme**
right click on the file and click extract here
press Alt + F2
type ~/.themes
copy the new folder on your desktop in there.
select new theme in theme manager

**icon theme**
right click on the file and click extract here
press Alt + F2
type ~/.icons
copy the new folder on your desktop in there.
select new theme in theme manager

**GDM theme**
System --> Administration --> Login Window
you can install it from there

If this seems too difficult try going to art.gnome.org to get your themes.  Every theme I have got from there works with drag and drop

If you are only wanting to change some colors here or there check out gnome-color-chooser ([http://gnome-look.org/content/show.php?content=47349](http://gnome-look.org/content/show.php?content=47349))

---

### Post by Zzl1xndd on 2007-01-09
if Im understanding you want to just change the colour of your menu bars. If so just right click on them go to properties > background > select solid colour > & select the coliur you want. (also make sure its set to opaque and not transperent.

---

### Post by jordanmthomas on 2007-01-09
good notice:  I just read the first response and expanded on it.
gnome-color-chooser will help though if you have black text on your panels.

---

### Post by featherking on 2007-01-20
i tried making a deb file for gnome-color-chooser, i had posted it in another thread. I will post a copy here too

---

