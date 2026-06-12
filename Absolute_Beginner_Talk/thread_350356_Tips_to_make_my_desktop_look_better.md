---
title: "Tips to make my desktop look better?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Hallvor on 2007-01-31
Hello. 

Was hoping that someone more creative than me could lead me on the right path to a better looking desktop. I have attached an image of my current desktop, so feel free to make suggestions. I am mainly looking for suggestions when it comes to desklets, as I am not completely satisfied with the ones I am using. (Can`t find a way to make them a little bigger.) But any constructive feedback is apperciated. :)

---

### Post by Minyaliel on 2007-01-31
Well, if you want a _really_ handsome desktop, try and take a look at the Elbuntu project @ [http://e17blog.tuxfamily.org/ebuntu_en.php/](http://e17blog.tuxfamily.org/ebuntu_en.php/). Animated backgrounds, real transparency, animated whateveryouwants, and it doesn't hog up your system.

---

### Post by maruchan on 2007-01-31
Hi Hallvor,

You could take a look at a site like gnome-look.org or art.gnome.org for screenshots and see what you like.

[http://www.gnome-look.org/index.php?xcontentmode=100](http://www.gnome-look.org/index.php?xcontentmode=100)  <-- lots of themes shown here

For wallpaper, I like InterfaceLift.

Sorry I don't know much about desklets - I don't really use them because I like an empty desktop.

---

### Post by lyceum on 2007-01-31
> **Minyaliel said:**
> Well, if you want a _really_ handsome desktop, try and take a look at the Elbuntu project @ [http://e17blog.tuxfamily.org/ebuntu_en.php/](http://e17blog.tuxfamily.org/ebuntu_en.php/). Animated backgrounds, real transparency, animated whateveryouwants, and it doesn't hog up your system.

If you do not want to wait for Elbuntu try this:

[http://ubuntuforums.org/showthread.php?t=319336&highlight=E17](http://ubuntuforums.org/showthread.php?t=319336&highlight=E17)

I like your desktop myself. Looks nice.

---

### Post by IYY on 2007-01-31
You could go to [www.gnome-look.org](www.gnome-look.org) and search for new GTK2 and Metacity themes, sorted by rating or popularity. Some of them are really beautiful.

deviantart has great wallpapers, again, it's best to sort by rating.

[http://browse.deviantart.com/?catpath=customization/wallpaper/&order=9&alltime=yes](http://browse.deviantart.com/?catpath=customization/wallpaper/&order=9&alltime=yes)

---

### Post by Hallvor on 2007-01-31
Thanks to all of you. Some of the themes on [http://www.gnome-look.org](http://www.gnome-look.org) look very nice, so I wouldn`t mind experimenting a little. But excactly how would I activate them once downloaded? And would it be easy to revert to my current desktop if I want it back?

Just curious...

---

### Post by ComplexNumber on 2007-01-31
> **Hallvor said:**
> Thanks. Some of the themes look very nice, so I wouldn`t mind experimenting a little. But excactly how would I activate them once downloaded? And would it be easy to revert to my current desktop if I want it back?

Just curious...
most of the themes come in a tarball where the package that you download looks something like this: some-theme.tar.gz. its just a compression file like zip. when you've downloaded it into your home directory, right click on the theme and select 'extract here'. then place the themes from the extracted contents in the .themes directory in your home directory. then if you go to 'Themes' in your menu (ie main menu -< system -> preferences -> themes), you will see it show up there where you can select them.
HOWEVER, themes need a theme engine to render properly. therefore, before you do the above, i recommend that you go to synaptic package manager (in the menu its in system -> administration -< synaptic) and do a search on Name Only for "gtk2-engine". install all them except gtk2-engines-gtk-qt.

---

### Post by Hallvor on 2007-01-31
Thanks again! Ubuntu "support" is just incredible. :)

---

### Post by maruchan on 2007-01-31
With many themes you can also just drag the .tar.gz file onto the theme manager and it will auto-install.

---

### Post by ComplexNumber on 2007-02-01
> **maruchan said:**
> With many themes you can also just drag the .tar.gz file onto the theme manager and it will auto-install.
thats not the recommended way, though, because it can't handle it when there is more than one theme or is in one standard format. for example, try to install [this]("http://gnome-look.org/content/show.php?content=48681") via gnome-theme-manager and you will see what i mean.

---

