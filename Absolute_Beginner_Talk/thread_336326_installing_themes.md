---
title: "installing themes"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by ENN0 on 2007-01-11
Hello again i have just downloaded 2 themes from GNOME look org. and want to know how to install the...what i have done so far is go to themes and click install theme i click on the folder of the theme and it opens it up...i have clicked on everything but it says "this file format is invalid!

---

### Post by ciscosurfer on 2007-01-11
> **ENN0 said:**
> Hello again i have just downloaded 2 themes from GNOME look org. and want to know how to install the...what i have done so far is go to themes and click install theme i click on the folder of the theme and it opens it up...i have clicked on everything but it says "this file format is invalid!Two points: first, you should install the theme in its compressed state (if it's a .tar.gz, then leave it that way, don't gunzip the file)...and remember, you can always do a drag and drop of the .tar.gz onto the main Themes window to install.  Second, the theme you are trying to install might either be in the wrong format or is a theme for KDE or some other WM.

---

### Post by meborc on 2007-01-11
what fileformat were they? sometimes bad files are uploaded to gnome-look... sometimes you need to unpack a tar to get more tars :) yeah it sounds crazy... anyway, the best way to do it is to download the file to your desktop... open the themes dialog and drag-drop the file there... then it will install and you can delete the file... OR it says it is the wrong file format and you need to unpack the tar...

hope i made any sense ;)

EDIT: ahh... i was too slow

---

### Post by ComplexNumber on 2007-01-11
the most reliable way is NOT to install them via gnome-theme-manager because it can't handle tarballs that have more than 1 file when it is compressed. the best way is to unpack it yourself and then transfer the contents to either /home/<your-username>/.themes or /usr/share/themes. to transfer them to /usr/share/themes, use 'sudo cp -R <theme names> /usr/share/themes' on the command line.

---

### Post by blackened on 2007-01-12
> **ComplexNumber said:**
> the most reliable way is NOT to install them via gnome-theme-manager because it can't handle tarballs that have more than 1 file when it is compressed. the best way is to unpack it yourself and then transfer the contents to either /home/<your-username>/.themes or /usr/share/themes. to transfer them to /usr/share/themes, use 'sudo cp -R <theme names> /usr/share/themes' on the command line.

I find that manually unpacking the tarballs to $HOME/.themes or usr/share/themes is much more convenient than having to suffer different peoples, sometimes arbitrary, packing schemes and how that interferes with the drag-and-drop method.

Also to note, if there is more than one user on your system and you want all users to have access to all themes, then it's best to manually unpack them to usr/share/themes. If you unpack them (or use the dnd method I think) they will be installed to $HOME/.themes and will only be accessible by that particular user.

---

