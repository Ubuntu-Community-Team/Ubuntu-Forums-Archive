---
title: "Few questions about creating Gtk themes"
date: 2005-02-10
forum: Art &amp; Design
---

### Post by minio on 2005-02-10
I'trying to make my own theme so i have few questions:

Is there any HOWTO?
Is there any list of all widgets and options i can use for it?
Does anybody know name of the widget in file-roller which is located under toolbar and contains back, forward, up and home buttons and location bar? It refuses to adapt.  :-| 

Thanks

---

### Post by bvc on 2005-02-10
Docs and tuts are thin...
Please add to this any tips or links you find useful. To start...

general -stuff
[http://www.gnomefiles.org/](http://www.gnomefiles.org/)
[http://www.gnomefiles.org/app.php?soft_id=114](http://www.gnomefiles.org/app.php?soft_id=114)

SmoothEngine
[http://gnome.org/~thos/Smooth-Docs/](http://gnome.org/~thos/Smooth-Docs/)
[http://www.unit-e.cc/~ajgenius/Gnome/Theme...id=SmoothEngine](http://www.unit-e.cc/~ajgenius/Gnome/Themes/Tutorials/?id=SmoothEngine)
[http://sourceforge.net/projects/smooth-engine/](http://sourceforge.net/projects/smooth-engine/)
[http://www.gnomefiles.org/app.php?soft_id=114](http://www.gnomefiles.org/app.php?soft_id=114)
[http://web.subpop.net/art/smoothgnome/](http://web.subpop.net/art/smoothgnome/)

GTK
[http://www.unit-e.cc/~ajgenius/Gnome/Theme...s/?id=GTKThemes](http://www.unit-e.cc/~ajgenius/Gnome/Themes/Tutorials/?id=GTKThemes)

Metacity
[http://developer.gnome.org/doc/tutorials/m...ity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

ICONS
[http://www.unit-e.cc/~ajgenius/Gnome/Theme.../?id=IconThemes](http://www.unit-e.cc/~ajgenius/Gnome/Themes/Tutorials/?id=IconThemes)
[http://www.gnomefiles.org/app.php?soft_id=385](http://www.gnomefiles.org/app.php?soft_id=385)
[http://gnomesupport.org/forums/viewtopic.p...hlight=standard](http://gnomesupport.org/forums/viewtopic.php?t=7397&highlight=standard)
[http://gnomesupport.org/forums/viewtopic.p...hlight=standard](http://gnomesupport.org/forums/viewtopic.php?t=7398&highlight=standard)
[http://developer.gnome.org/doc/API/2.4/gtk...tock-Items.html](http://developer.gnome.org/doc/API/2.4/gtk/gtk-Stock-Items.html)

Help other than here
[http://gnomesupport.org/forums/viewforum.php?f=20](http://gnomesupport.org/forums/viewforum.php?f=20)

Tinkering and hacking others themes is necessary to really get it. Docs are very limited. So get stuff and hack! That's what I did.
[http://gnome-look.org/](http://gnome-look.org/)
[http://art.gnome.org/](http://art.gnome.org/)
[http://www.themedepot.org/](http://www.themedepot.org/)

**[color=blue][size=7]GNOME ROCKS![/size][/color]**

you need images to play with/practice/port for pixmap themes?
[http://www.wincustomize.com/skins.asp?library=1](http://www.wincustomize.com/skins.asp?library=1)
the .wba extension is seen as a zip type by file-roller ;)

_**Errors**_
Whether gtk, metacity, or icon theming, errors may or may not be printed in vt1 (Ctrl+Alt+F1) depending on the distro you use. Mandrake used to, but doesn't seem to anymore. Debian's and Fedora do. You can easily get the errors by running
gnome-theme-manager
in an X terminal (Gnome Terminal, Aterm, Eterm, Xterm, rxvt etc....).

_*Metacity*_
Metacity has a nice tool. The
metacity-theme-viewer
Run it from an X terminal;
metacity-theme-viewer name_of_metacity_theme
[example]metacity-theme-viewer d3a
and you can find out how fast it loads and errors pointing to any problems with loading the theme. It opens a gui to show you all the different aspects of the theme.

[http://developer.gnome.org/projects/gup/hig/1.0/](http://developer.gnome.org/projects/gup/hig/1.0/)
[http://cvs.gnome.org/viewcvs/gtk+/docs/wid...try.txt?rev=1.5](http://cvs.gnome.org/viewcvs/gtk+/docs/widget_geometry.txt?rev=1.5)

##################
**Scalable Vector Graphics**
you can make svg/gtk and metacity themes, and of course icon themes.

[http://librsvg.sourceforge.net/](http://librsvg.sourceforge.net/)
[http://www.inkscape.org/](http://www.inkscape.org/) (has a built in tutorial)
[http://www.sodipodi.com/](http://www.sodipodi.com/)

[http://programmer-art.org/?page=inkscape](http://programmer-art.org/?page=inkscape)

If you mean engines...I have no idea, except to learn gtk and read it's docs

---

### Post by minio on 2005-02-12
Great   :grin:   . Thanks a lot.  :grin:  Maybe you should make a sticky thread with this list. I haven't seen list like this on any site where i would expect it - gnome, gtk, gnome-look, art.gnome... I have nothing to add, maybe only suggestion for metacity themes to start with industrial,human, or other industrial based themes, since they  IMHO show most of what is posible to do with metacity without using pixmaps and they code is well arranged. Thanks again :-)

---

