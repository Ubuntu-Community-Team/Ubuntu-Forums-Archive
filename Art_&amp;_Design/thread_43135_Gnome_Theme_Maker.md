---
title: "Gnome Theme Maker?"
date: 2005-06-20
forum: Art &amp; Design
---

### Post by XDevHald on 2005-06-20
This is my n00b question for the day. Where can I download a Gnome theme maker?

---

### Post by Alexander Kirillov on 2005-06-21
[QUOTE=BB]This is my n00b question for the day. Where can I download a Gnome theme maker?[/QUOTE]
 I do not think such a thing exists - the best resource I know of is the tutorial here:
[http://live.gnome.org/GnomeArt_2fTutorials_2fGtkThemes](http://live.gnome.org/GnomeArt_2fTutorials_2fGtkThemes)

---

### Post by XDevHald on 2005-06-21
Thank you for the reply!

---

### Post by bvc on 2005-06-21
**_Metacity Theme Editor_**
[http://gnomesupport.org/forums/viewtopic.php?t=9400&highlight=](http://gnomesupport.org/forums/viewtopic.php?t=9400&highlight=)



I posted this here, and on another forum
Please add to this any tips or links you find useful. To start...

general (know the environment)
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


you need images for pixmap themes and practice?
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
This is what I'm currently interested in and researching. Instead of pixmap, you can make svg/gtk and metacity themes, and of course icon themes.

[http://librsvg.sourceforge.net/](http://librsvg.sourceforge.net/)
[http://www.inkscape.org/](http://www.inkscape.org/) (has a built in tutorial)
[http://www.sodipodi.com/](http://www.sodipodi.com/)

[http://programmer-art.org/?page=inkscape](http://programmer-art.org/?page=inkscape)

---

### Post by bvc on 2005-06-24
oh, and GIB
[http://gnomefiles.org/app.php?soft_id=385](http://gnomefiles.org/app.php?soft_id=385)
if the downlaod isn't available I have them here
[http://kwh.kernow-gb.com/~bvc/theme/icons/gib/](http://kwh.kernow-gb.com/~bvc/theme/icons/gib/)

---

### Post by aledie on 2005-06-26
[QUOTE=bvc]oh, and GIB
[http://gnomefiles.org/app.php?soft_id=385](http://gnomefiles.org/app.php?soft_id=385)
if the downlaod isn't available I have them here
[http://kwh.kernow-gb.com/~bvc/theme/icons/gib/](http://kwh.kernow-gb.com/~bvc/theme/icons/gib/)[/QUOTE]


I have installed GIB, but it doesn't start. All packages needed are installed also (like Mono). Any suggestions?

---

### Post by bvc on 2005-06-27
are you starting it per instructions?
cd /path/to/gib
mono gib.exe

if so what are the errors? It's always worked for me on ubuntu from pre-warty to hoary.

---

### Post by aledie on 2005-06-27
[QUOTE=bvc]are you starting it per instructions?
cd /path/to/gib
mono gib.exe

if so what are the errors? It's always worked for me on ubuntu from pre-warty to hoary.[/QUOTE]


Hi bvc, I am using hoary. I have mono packages installed (mono, mono-assemblies-base, mono-common, mono-jit). 
[B]
1. I tried it per instructions. Here are the errors:[/B] . Dont know how far it would affect its functions:[/B]

alex@alex:~/My Downloads/ico/gib-0.2-bin$ mono gib.exe

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_locate_file: assertion `program != NULL' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_locate_file: assertion `program != NULL' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GConf-CRITICAL **: gconf_escape_key: assertion `arbitrary_text != NULL' failed

(<unknown>:29015): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_accel_map_add_entry: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_widget_set_accel_path: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_accel_map_add_entry: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_widget_set_accel_path: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_accel_map_add_entry: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_widget_set_accel_path: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_accel_map_add_entry: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_widget_set_accel_path: assertion `_gtk_accel_path_is_valid (accel_path)' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(<unknown>:29015): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(<unknown>:29015): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(<unknown>:29015): Gtk-CRITICAL **: gtk_widget_set_accel_path: assertion `_gtk_accel_path_is_valid (accel_path)' failed


2. Now maybe it is coused by errors in installation, GIB crashes quite often. Also if I click preferences, I just get a message window "Image size" with two buttons "help" and "close". Both buttons don't work. 

3. I have read GIB has a function to convert a KDE icon theme to GNOME. How does it work? I would like to convert KDE icons. 

Sorry for so many questions. Thank you

---

### Post by bvc on 2005-06-28
no gib has always crashed all the time.....save your work very often. I just had it delete everything in an index.theme file :|

I also have found that I have to use both versions to get a theme done from start to finish.

I've never looked at the convert a kde theme feature

---

### Post by jolofj on 2012-08-23
[http://linux.softpedia.com/get/Desktop-Environment/Tools/Metacity-Themer-45633.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Metacity-Themer-45633.shtml)

---

### Post by sffvba[e0rt on 2012-08-23
[IMG]http://i299.photobucket.com/albums/mm313/Zenzirouj/ThreadNecro.gif[/IMG]


404

---

