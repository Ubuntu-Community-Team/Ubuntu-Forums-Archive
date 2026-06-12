---
title: "Help installing Gimp Normalmap plugin"
date: 2008-01-14
forum: Art &amp; Design
---

### Post by person_99 on 2008-01-14
I hate having to do normal maps by hand, and I want to used this tool I previously had on an install of Windows.

Found at: [http://nifelheim.dyndns.org/~cocidius/normalmap/](http://nifelheim.dyndns.org/~cocidius/normalmap/)

The only download for linux available is the source code, and I am not sure at all on how to compile it.

When I go to the folder (Extracted from the tar.bz2) and do make, I get the following error messages:

 ```
gcc -c -O3 -Wall `pkg-config --cflags gtk+-2.0 gtkglext-1.0 gimp-2.0` normalmap.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtkglext-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkglext-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkglext-1.0' found
Package gimp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gimp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gimp-2.0' found
normalmap.c:26:21:
 
error: 
gtk/gtk.h: No such file or directory

normalmap.c:28:26:
 
error: 
libgimp/gimp.h: No such file or directory

normalmap.c:29:28:
 
error: 
libgimp/gimpui.h: No such file or directory

In file included from normalmap.c:32:
preview3d.h:25: error: expected ')' before '*' token

normalmap.c:66: error: expected specifier-qualifier-list before 'gint'

normalmap.c:82: warning: type defaults to 'int' in declaration of 'gchar'

normalmap.c:82: error: expected ';', ',' or ')' before '*' token

normalmap.c:85: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'normalmap'

normalmap.c:87: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'normalmap_dialog'

normalmap.c:89: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'PLUG_IN_INFO'

normalmap.c:96: error: unknown field 'filter' specified in initializer

normalmap.c:96: warning: excess elements in struct initializer

normalmap.c:96: warning: (near initialization for 'nmapvals')

normalmap.c:97: error: unknown field 'minz' specified in initializer

normalmap.c:97: warning: excess elements in struct initializer

normalmap.c:97: warning: (near initialization for 'nmapvals')

normalmap.c:98: error: unknown field 'scale' specified in initializer

normalmap.c:98: warning: excess elements in struct initializer

normalmap.c:98: warning: (near initialization for 'nmapvals')

normalmap.c:99: error: unknown field 'wrap' specified in initializer

normalmap.c:99: warning: excess elements in struct initializer

normalmap.c:99: warning: (near initialization for 'nmapvals')

normalmap.c:100: error: unknown field 'height_source' specified in initializer

normalmap.c:100: warning: excess elements in struct initializer

normalmap.c:100: warning: (near initialization for 'nmapvals')

normalmap.c:101: error: unknown field 'alpha' specified in initializer

normalmap.c:101: warning: excess elements in struct initializer

normalmap.c:101: warning: (near initialization for 'nmapvals')

normalmap.c:102: error: unknown field 'conversion' specified in initializer

normalmap.c:102: warning: excess elements in struct initializer

normalmap.c:102: warning: (near initialization for 'nmapvals')

normalmap.c:103: error: unknown field 'dudv' specified in initializer

normalmap.c:103: warning: excess elements in struct initializer

normalmap.c:103: warning: (near initialization for 'nmapvals')

normalmap.c:104: error: unknown field 'xinvert' specified in initializer

normalmap.c:104: warning: excess elements in struct initializer

normalmap.c:104: warning: (near initialization for 'nmapvals')

normalmap.c:105: error: unknown field 'yinvert' specified in initializer

normalmap.c:105: warning: excess elements in struct initializer

normalmap.c:105: warning: (near initialization for 'nmapvals')

normalmap.c:106: error: unknown field 'swapRGB' specified in initializer

normalmap.c:106: warning: excess elements in struct initializer

normalmap.c:106: warning: (near initialization for 'nmapvals')

normalmap.c:107: error: unknown field 'contrast' specified in initializer

normalmap.c:107: warning: excess elements in struct initializer

normalmap.c:107: warning: (near initialization for 'nmapvals')

normalmap.c:108: error: unknown field 'alphamap_id' specified in initializer

normalmap.c:109: warning: excess elements in struct initializer

normalmap.c:109: warning: (near initialization for 'nmapvals')

normalmap.c:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'runme'

normalmap.c:115: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token

normalmap.c:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token

normalmap.c:120: warning: return type defaults to 'int'

normalmap.c: In function 'MAIN':

normalmap.c:121: error: expected '=', ',', ';', 'asm' or '__attribute__' before '{' token

normalmap.c:156: warning: type defaults to 'int' in declaration of 'gchar'

normalmap.c:156: error: expected ';', ',' or ')' before '*' token

normalmap.c:239: error: expected '=', ',', ';', 'asm' or '__attribute__' before '{' token

normalmap.c:257: error: storage class specified for parameter 'kernel_element'

normalmap.c:259: error: expected ')' before '*' token

normalmap.c:276: error: expected '=', ',', ';', 'asm' or '__attribute__' before '{' token

normalmap.c:292: error: expected '=', ',', ';', 'asm' or '__attribute__' before '{' token

normalmap.c:335: error: expected '=', ',', ';', 'asm' or '__attribute__' before '{' token

normalmap.c:461: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'normalmap'

normalmap.c:1130: error: expected ')' before 'data'

normalmap.c:1136: error: storage class specified for parameter 'update_preview'

normalmap.c:1136: error: parameter 'update_preview' is initialized

normalmap.c:1138: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'idle_callback'

normalmap.c:1148: error: expected ')' before '*' token

normalmap.c:1157: error: expected ')' before '*' token

normalmap.c:1163: error: expected ')' before '*' token

normalmap.c:1169: error: expected ')' before '*' token

normalmap.c:1192: error: expected ')' before '*' token

normalmap.c:1201: error: expected ')' before '*' token

normalmap.c:1214: error: expected ')' before '*' token

normalmap.c:1225: error: expected ')' before '*' token

normalmap.c:1252: error: expected ')' before '*' token

normalmap.c:1258: error: expected ')' before '*' token

normalmap.c:1264: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'dialog_constrain'

normalmap.c:1276: error: expected ')' before 'id'

normalmap.c:1285: error: expected ')' before '*' token

normalmap.c:1298: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'normalmap_dialog'

normalmap.c:1136: error: declaration for parameter 'update_preview' but no such parameter

normalmap.c:257: error: declaration for parameter 'kernel_element' but no such parameter

normalmap.c:1779: error: expected '{' at end of input

make: *** [normalmap.o] Error 1

```

Note: Before you ask me to just do it in Windows:
My Windows crashed yesterday. It somehow managed to corrupt it's own registry right after a reinstall for the 3rd time that day.

Can anyone help me get this working?

---

### Post by smartboyathome on 2008-01-14
I looked at it, and I think it won't work with GIMP since it installs to a previous version of GTK/GIMP. I will look at it again tomarrow to make sure I didn't miss anything).

---

### Post by Paul820 on 2008-01-14
I have the gimp normalmap plugin working on gimp 2.4.2, the normalmap plugin version is 2.0. To build the plugin you must have these libraries installed.
> libgimp2.0-dev
libglew1.4-dev
libgtk2.0-dev

Then it's just a cas of **make** and **make install**

It does work as you can see from the following screenshot, if you need more help let me know.

---

### Post by Paul820 on 2008-01-14
I got the plugin version wrong, i am using the most recent version. The 2.0 version i wrote above was the gimp version it ran under. Sorry for the confusion, i just thought i would clear that up.

---

### Post by person_99 on 2008-01-14
I am running in Gimp 2.2.
How can I upgrade to 2.4?

---

### Post by Paul820 on 2008-01-14
You don't need to upgrade. The plugin should work with gimp version 2.0.x and above like it says on the website. Have you tried building it again with those development files that i said you needed? Oh, and you also need **build-essential**, i don't know if you have that already.

---

