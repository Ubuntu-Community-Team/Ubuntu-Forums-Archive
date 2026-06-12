---
title: "compiz for kde"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by uchiha_sasuke on 2007-12-01
hi
i am new to linux and installed gutsy just today and installed some packages.
i downloaded compiz manager for enhanced desktop.i then got KDE kubuntu .but i cannot get the same effects here.i downloaded and installed compiz-kde also . it did not make a difference .need some help.thnx in advance.if any commands are involved plz post them along

---

### Post by ajopaul on 2007-12-01
> **uchiha_sasuke said:**
> hi
i am new to linux and installed gutsy just today and installed some packages.
i downloaded compiz manager for enhanced desktop.i then got KDE kubuntu .but i cannot get the same effects here.i downloaded and installed compiz-kde also . it did not make a difference .need some help.thnx in advance.if any commands are involved plz post them along

First of all, you should check if your graphics card can support compiz. to do that type
```
glxinfo | grep render
```. if the answer is yes proceed by typing ```
compiz --replace
``` if alls well you should have the compizfusion enabled. To configure compiz install the following packages ```
compiz-fusion-plugins-extra compizconfig-settings-manager
```

---

### Post by ajopaul on 2007-12-01
if got a answer as no and if your graphics card is ATI/nVidia make sure the package restricted-manager-kde is installed, then launch the same and enable the appropriate drivers

---

### Post by uchiha_sasuke on 2007-12-02
ya my graphics card is supported i had downloaded nvidia glx new and compiz worked in gnome properly but i am having problems in kde.i did as you told here is the terminal output
rakeshvarna@rakeshvarna-laptop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Quadro NVS 140M/PCI/SSE2
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
rakeshvarna@rakeshvarna-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0429 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting kde-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


here the terminal hangs .

---

