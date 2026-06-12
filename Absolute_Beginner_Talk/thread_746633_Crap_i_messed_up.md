---
title: "Crap i messed up"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by stevesmall on 2008-04-05
Ok guys i had a perfectly working ubuntu 7.10 gutsy running on my laptop and i couldnt get my svideo out to display on a tv so like a moron i opened up my graphics card manager and started playing well  i messed it up bad. SO i said whatever and i did a fresh reinstall of ubuntu. But now i have a problem i cant get compiz-Fusion to work. If i go to system/ preferences i have a button for compiz config settings manager which when i click it does nothing and another button saying compiz settings manager and when i click that it says Dbus failed to load  Compiz is not running the dbus plug in can not be activated unless compiz is running. but if i click close on it a compiz settings box does open with a few options like wobbly scale fade. Even though wobbly is ticked and enabled the windows has no effect. i know its probably something stupid on my part but i request the help of you fine ubuntu gods. Also unlike last time i have no advanced appearance button

---

### Post by 1875 on 2008-04-05
I assume you have enabled any restricted drivers that are available ?

---

### Post by skymera on 2008-04-05
What is your graphics card?

---

### Post by stevesmall on 2008-04-05
intel GMA 950 graphics card and yes all my restricted drivers are enabled its weird cause it worked two days ago perfectly before the restore

---

### Post by stevesmall on 2008-04-06
I had this graphics card installed with the first ubuntu install and it worked perfect not sure how i messed up

---

### Post by JoshuaRL on 2008-04-06
Can you go into Add/Remove Applications and search for "compiz"?  The Advanced Settings Manager should be in there.  See if that fixes it.

---

### Post by stevesmall on 2008-04-06
the weird thing is compiz dont show up in my add remove programs alot of things are missing. Its weird cause i do have universe repositorys on

---

### Post by JoshuaRL on 2008-04-06
Okay, go into System->Settings->Software Sources and make sure you have everything except the install CD and source code enabled.

Then go to System->Administration->Update Manager and make sure everything is installed.

After that, try going back into Add/Remove Applications again and see if Compiz is there.

---

### Post by stevesmall on 2008-04-06
> **JoshuaRL said:**
> Okay, go into System->Settings->Software Sources and make sure you have everything except the install CD and source code enabled.

Then go to System->Administration->Update Manager and make sure everything is installed.

After that, try going back into Add/Remove Applications again and see if Compiz is there.

Nope followed all steps listed in your post and still nothing i cant figure it out for the life of me.

---

### Post by JoshuaRL on 2008-04-06
Okay, try this from the Terminal:
```

apt-cache search compiz

```

---

### Post by stevesmall on 2008-04-06
this is what that spit out


compiz-fusion-plugins-main - Collection of plugins from OpenCompositing for Compiz
libcompizconfig0 - Settings library for plugins - OpenCompositing Project
libcompizconfig0-dev - Development file for plugin settings - OpenCompositing Project
cairo-clock - An analog clock drawn with vector-graphics
compiz-compcomm-plugins-main - Collection of plugins from OpenCompositing for Compiz
emerald - Decorator for compiz-fusion
gnome-compiz-manager - Compiz Gnome Manager
libcm-dev - Support code for compositing managers - development files
libcm7 - Support code for compositing managers
libemeraldengine0 - Decoration engines for compiz-fusion
libgnome-compiz-manager0 - Compiz Gnome Manager
libgnome-compiz-manager0-dev - Compiz Gnome Manager
pdfcube - PDF document viewer with 3D effects
python-compizconfig - Compiz configuration system bindings
compiz - OpenGL window and compositing manager
compiz-core - OpenGL window and compositing manager
compiz-dev - OpenGL window and compositing manager - development files
compiz-fusion-plugins-extra - Collection of extra plugins from OpenCompositing for Compiz
compiz-gnome - OpenGL window and compositing manager - GNOME window decorator
compiz-plugins - OpenGL window and compositing manager - plugins
libdecoration0 - Compiz window decoration library
libdecoration0-dev - Compiz window decoration library - development files
compiz-kde - OpenGL window and compositing manager - KDE window decorator
kicker-compiz - modified pager applet for Kicker made to work with Compiz
kicker-taskbar-compiz - modified Kicker taskbar applet made to work with compiz
screenlets - Widget-like mini-applications for GNOME
compiz-bcop - Compiz option code generator
libcompizconfig-backend-gconf - GNOME Backend for the Compiz Configuration System
libcompizconfig-backend-kconfig - KDE Backend for the Compiz Configuration System
compizconfig-settings-manager - Plugin and configuration tool - Compiz Fusion Project
compiz-settings - Compiz Configuration tool


hey wait a second isnt there if i remember correctly a misnamed file somewhere im supposed to delete a character from

---

