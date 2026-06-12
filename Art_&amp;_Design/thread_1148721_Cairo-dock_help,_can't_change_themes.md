---
title: "Cairo-dock help, can't change themes"
date: 2009-05-04
forum: Art &amp; Design
---

### Post by ElevenWarrior on 2009-05-04
Hello everyone, I'm running 9.04 64-bit, and with Cairo-dock 2.0.0
When I go to change my themes I get this error,

warning : (cairo-dock-themes-manager.c:cairo_dock_get_theme_path:733)
couldn't retrieve distant theme Tux_n_Tosh : an error occured while executing ' wget "http://themes.cairo-dock.org//Tux_n_Tosh/Tux_n_Tosh.tar.gz" -O "/tmp/cairo-dock-net-file.z9NDNJ" -t 2 -T 3'
on_theme_apply: assertion `cNewThemePath != NULL' failed
on_click_normal_quit ()
on_delete_normal_gui ()

the theme never changes. :(
thanks in advance

---

### Post by fabounet on 2009-05-05
which version ?
Cairo-Dock2 is currently being released, so be sure to have the last RC.

---

### Post by ElevenWarrior on 2009-05-06
I haver verison. ah thank you! I think thats it.
( had RC1)

---

### Post by shomy on 2009-05-27
Hi guys i got cairo dock working with themes here are the steps used to solve the problem.

1. download cairo-dock 2+
2. download cairo-dock2+ plugins
3. sudo apt-get install xterm   (it apparently uses xterm download the actual theme files.

4. YAY!!


hope this helps you all

---

