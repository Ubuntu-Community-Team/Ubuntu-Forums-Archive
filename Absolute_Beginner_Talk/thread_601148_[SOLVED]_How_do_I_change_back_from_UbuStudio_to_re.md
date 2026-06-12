---
title: "[SOLVED] How do I change back from UbuStudio to regular Ubuntu Gutsy?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by JimBuntu on 2007-11-02
How can I change my system from Ubuntu Studio Gutsy to regular Ubuntu Gutsy? I like the programs that Studio cam with and I like the look, but I would rather have the brown theme and wallpaper. Also, if I can change from Studio I want to keep all my programs and files. Is this possible?

---

### Post by defrex on 2007-11-02
I imagine that the theme manager (system>preferences>appearance) of Ubuntu Studio probably has the human theme (the default Ubuntu theme). If not, the package *ubuntu-desktop* is an umbrella package that'll probably have the theme in it. Then you can just change it in the theme manager.

---

### Post by JimBuntu on 2007-11-02
human theme is not there.

---

### Post by JimBuntu on 2007-11-03
if i install the ubuntu-desktop package will that remove all of the programs that i already have installed? It looks like its going to install all of the programs that come with the original ubuntu desktop but some of them it says its installing when i already have them.

---

### Post by MrFSL on 2007-11-03
Search the repository...

Here is the example:
```
apt-cache search ubuntu | grep -i theme | sort
```

It returned the following for me and my repositories:
> blubuntu-gdm-theme - Blubuntu look - GDM theme
blubuntu-theme - Blubuntu look - GTK and Metacity theme
edubuntu-artwork - edubuntu themes and artwork
firefox-themes-ubuntu - Firefox themes matching the Ubuntu desktop look
gfxboot-theme-ubuntu - Ubuntu theme for gfxboot-compliant boot loaders
gtk2-engines-murrine - 'murrine' theme engine for GTK+ 2.x
gtk2-engines-ubuntulooks - 'ubuntulooks' theme for GTK+ 2.x
human-icon-theme - Human Icon theme
human-theme - Human theme
tangerine-icon-theme - Tangerine Icon theme
tango-icon-theme-common - Tango Icon theme - common icons
ubuntu-artwork - Ubuntu themes and artwork
ubuntu-calendar - The Ubuntu Calendar features monthly updated artwork and themes
ubuntu-sounds - Ubuntu's GNOME audio theme
ubuntustudio-icon-theme - UbuntuStudio Icon theme
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
usplash-theme-ubuntu - Usplash theme for Ubuntu
xubuntu-artwork - Xubuntu themes and artwork


My guess would be a:
```
sudo apt-get install  human-theme
```

---

### Post by numbah_one's on 2007-12-08
how can i remove blubuntu,its conflicting with my awn...

---

