---
title: "Are themes bug free"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by comfixit on 2006-11-27
I want to change the look of my Ubuntu. I am running Edgy. There are some nice looking themes at [http://gnome-look.org/](http://gnome-look.org/)

My questions are:

* I have used early incarnations of WindowsBlinds in Windows and have found that certain designs could be buggy. Do I need to have similar concerns with themes downloaded from Gnome Look?

* Is everything packaged as a single download? For example the background, icons, splash screens etc... or do you kind of need to mix and match when you create a screen? If so what are the major theme components?

* What types of themes as an Ubuntu Edgy default installation user should I be looking for? (GTK 2.0 based?)

Thanks in advance for any help or advice offered on this matter.

---

### Post by Ben Sprinkle on 2006-11-27
There should be no bugs unless you find one or they post it, usually all is good.
And yes, GTK 2 based. :)

There are several engines out there which look half decent also.
There usually in a .tar.gz or .tgz or .gz, which you extract that folder into /usr/share/themes .

---

### Post by CatKiller on 2006-11-27
They don't, in general, come with backgrounds.

As I understand it, a Gnome theme is generally made up of three parts - icons, a GTK bit and a Metacity bit (I'm not entirely sure what the difference is between the last two - I think one of them is the border and titlebar and one of them is the widgets in the window). Sometimes when you download a theme it will come with all three bits. Sometimes it's just one. Either way you can mix-and-match with the Theme Manager application.

If the themes have been packaged properly - like the ones from art.gnome. org are - then you don't even need to extract them - you can drag-and-drop the tar.gz file on the Theme Manager window and it will be installed automagically. Otherwise, you can extract the file to either ~/.themes or ~/.icons, depending. There's a lot more information at art.gnome.org too.

All the GTK bits need to use a GTK engine (the GTK bits are configuration options for a particular engine). These are not usually included with the download, and a number of theme authors neglect to say which engine they are using. So if you install a theme and it looks crap, and nothing like their screenshot, it's probably because you don't have the theme engine installed that you need to use. There are a number of theme engines installable through Synaptic.

The login window is themeable too, and for Gnome you'd be looking for a GDM theme. This is chosen with the application at System -> Administration -> Login Window.

I believe the splash screen is just an image. You can select this with the application at System -> Preferences -> Splash Screen.

That's about all I know.

---

