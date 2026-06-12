---
title: "Themes and KDE"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by truNWA on 2006-07-14
I know this is a real n00bish question, but how do you add and change themes in KDE.

---

### Post by T700 on 2006-07-14
[SIZE=3][COLOR=Black]1) From a console go to the directory where you downloaded the package and type ```
sudo dpkg -i package_name.deb
``` replacing package_name with the one you downloaded.

2) From within KDE right click on the package then follow Kubuntu Package Menu-> Install Package.

Paul
[/COLOR][/SIZE]

---

### Post by Jucato on 2006-07-14
Depends on what "theme" you are trying to change. But all of them could be set using System Settings > Appearance group.

1. Icon themes: you will probably download these in .tar.gz archives. Go to System Settings > Appearance > Icons, click on Install New Theme, and look for the .tar.gz archive. Take note: don't extract/uncompress the icon themes. That will automatically be done for you

2. Color schemes: color schemes usually come in .kcsrc files (If you managed to get a .tar.gz, you have to extract it). Go to System Settings > Appearance > Colors, click on Import Scheme, and look for the .kcsrc file.

3. Style: KDE styles control how widgets (toolbars, tabs, buttons, menus, controls, etc) are displayed. In KDE-Look.org, they can be found under the "Themes/Styles" category. Most of the time they require compiling from source code, or just installation from a .deb or .rpm package. Once installed, they can be chosen from the drop-down list in System Settings > Appearance > Style.

4. Window Decorations: These controls the display of window borders, window title bars, and window buttons. There are different kinds of Window decoration themes. Native decorations would require some compilation and/or installation. They will appear as separate entries in the drop down list in System Settings > Appearance > Window Decorations. Another kind of theme is a deKorator theme. 

deKorator is a KDE window decoration engine. Basically what it does is allow you to create themes using pixmaps/small images and compile them into a theme of your own, or install pre-existing themes without having to compile. The only disadvantage of this is that you will be limited by what the deKorator engine can do. (But I guess it's more than what you need right?) deKorator themes come in .tar.gz (no need to extract). the deKorator engine can be installed from the repositories. Once installed and chosen from the drop-down list (in System Settings), you can install a downloaded theme from the Themes tab of deKorator.

5. GTK Styles and Fonts: Basically controls how GTK/GTK+ programs (like GNOME or Xfce stuff) are displayed and what fonts are used. These themes also need compilation and/or installation.

6. KDM Theme: This one is different from the rest, since it requires root/administrator privilege and is found in System Settings > System Administration group. But you have to install the package called *kdmtheme* before you can see it in System Settings. What this type of theme does is to control the display/appearance of your Login screen. These themes come in .tar.gz archives (again, no need to extract), and can simply be installed by going to System Settings > System Administration Group > KDM Theme Manager, clicking on Administrator Mode (enter your password) and clicking on Install New Theme.

6. Splash Screen: splash screens are the (sort of) animated screens that you see after you log in and before the whole desktop is displayed, the part where you see system messages like "loading desktop", etc. These themes come in .tar.gz archives (you know what I will say :D) and can be installed in System Settings > Display > Splash Screen and clicking on Add...

Hope that helps.

---

