---
title: "trouble with compiz"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-04
i installed compiz as follows:

#pacman -S compiz-core
#pacman -Sy compiz-manager


and then logged in as a non-root user.i opened up the terminal and typed in:
$compiz-manager

and it stated that Xgl was not found.The following is the exact output:

[sonujha@arch ~]$ compiz-manager
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0161 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


what is this?will i not be able to use compiz?

also,once installed,how do i configure compiz,i mean,say for example in ubuntu there is a program called compizconfig-settings-manager,but,how do i get that in arch?


i intend to use a GTK theme,and also an emerald theme.i will also have to add the folllowing to system>preferences>sessions>startup programs:

gtk-window-decorator --replace
compiz --replace --use-cow gconf

what does this do?also,tell me if i will be able to use compiz in conjunction with my GTK theme and emerald theme
?

---

### Post by smartboyathome on 2009-02-05
You want Compiz Fusion, not compiz-core. Install compiz fusion and the problems should go away. About XGL: you need to set it up in Xorg (look at the wiki).

See here: [http://wiki.archlinux.org/index.php/Compiz_Fusion](http://wiki.archlinux.org/index.php/Compiz_Fusion)

---

### Post by stonecoldjha on 2009-02-05
i did not get anything about Xgl in the arch wiki.i also tried googling around,but to no avail.

---

### Post by smartboyathome on 2009-02-05
[http://wiki.archlinux.org/index.php/Xgl_Troubleshooting](http://wiki.archlinux.org/index.php/Xgl_Troubleshooting) :)

---

### Post by stonecoldjha on 2009-02-05
but that's about troubleshooting.i haven't yet installed xgl.

---

### Post by stonecoldjha on 2009-02-05
i got it all donw,installed xgl with #pacman -S xgl,and then followed the guide above to install compiz-fusion.but when i launch it by
$fusion-icon,the following is the output:


[sonujha@arch ~]$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp
compiz (core) - Warn: No GLXFBConfig for depth 32
compiz (core) - Warn: No GLXFBConfig for depth 32
compiz (core) - Warn: No GLXFBConfig for depth 32
compiz (core) - Warn: No GLXFBConfig for depth 32
compiz (core) - Warn: No GLXFBConfig for depth 32
compiz (core) - Warn: No GLXFBConfig for depth 3

i can then see compiz in action(effects visible),but the terminal doesn't drop back to $.Moreover,my windows do not have any borders,as you can see in the screenshot.

how do i fix this?

---

### Post by smartboyathome on 2009-02-05
You will need to start compiz fusion the the '&' symbol at the end, and then run either 'gtk-window-decorator --replace' or 'emerald --replace'.

---

### Post by crimesaucer on 2009-02-05
Can I ask how you configured NVIDIA and xorg.conf?


Did you do it with this command:


```
nvidia-xconfig --composite
```


form this page: [http://wiki.archlinux.org/index.php/Composite#NVIDIA_drivers_.28proprietary.29](http://wiki.archlinux.org/index.php/Composite#NVIDIA_drivers_.28proprietary.29)

---

