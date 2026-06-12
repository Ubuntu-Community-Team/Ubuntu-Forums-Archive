---
title: "Removing something from my xubuntu menu"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-21
How do I remove shortcuts from my applications menu in xubuntu.  In Gnome, you have alacarte.  What do you have in XFCE?

---

### Post by Oldsoldier2003 on 2008-03-21
> **hikujk123 said:**
> How do I remove shortcuts from my applications menu in xubuntu.  In Gnome, you have alacarte.  What do you have in XFCE?


> While it is possible to edit the file manually, the recommended method for editing the menu.xml file is via the Xfce 4 Menu Editor, which can be started by running xfce4-menueditor, or using the "Edit desktop menu" button available from the Menu tab of the Desktop settings dialog. The menu editor also supports drag'n'drop from a file manager.
[http://www.xfce.org/documentation/4.2/manuals/xfdesktop](http://www.xfce.org/documentation/4.2/manuals/xfdesktop)

---

### Post by hikujk123 on 2008-03-21
That didn't do it.  That edits my top panel and settings section only., not the whole applications menu.

---

### Post by hikujk123 on 2008-03-23
Bump.  Right click > Edit Menu only display settings manager, Xubuntu Help, and Quit, it does not actually let me edit my applications menu.  I would like to remove a trillian icon (I uninstalled trillian under wine but the icon never went away).  Also, I would like to add MS Office icons under office.

---

### Post by hikujk123 on 2008-03-23
Bump.  Under my other meu, trillian is listed, even though I uninstalled it.

---

### Post by hikujk123 on 2008-03-24
Bump

---

### Post by hikujk123 on 2008-03-24
Still need help...Doesn't anyone know?

---

### Post by elliio on 2008-04-02
Hi, you might want to get some Popcorn and have a read. I've included a link to the Xfce wiki page for further info. :popcorn:

There's a way to edit the [COLOR=Red]/usr/share/applications/[/COLOR][COLOR=Magenta]APPLICATION_NAME[/COLOR][COLOR=Red].desktop[/COLOR] files, in your case it would be to edit [COLOR=Red]/usr/share/applications/trillian.desktop[/COLOR]

open the [COLOR=Red].desktop[/COLOR] file with mousepad as root:

```

[COLOR=Magenta]gksudo mousepad %d /usr/share/applications/trillian.desktop[/COLOR]

```or maybe try it without the %d (which passes the directory to the application)

```

[COLOR=Magenta]gksudo mousepad %d /usr/share/applications/trillian.desktop[/COLOR]

```and add the following to the bottom of the text in the .desktop file, which mousepad has opened as a text file (since everything in linux is a text file at the base level, you get these Super Cow Powers hehehe...).

text to enter at the bottom: 

```
[COLOR=Magenta]
NoDisplay=true
[/COLOR]
```or for example, if I wanted to NOT DISPLAY my GQView Xfce Desktop Menu, then I would [COLOR=DeepSkyBlue]NOT DELETE[/COLOR] the "[COLOR=Red]gqview.desktop[/COLOR]" file located in "[COLOR=Red]/usr/share/applications/[/COLOR]", but [COLOR=DeepSkyBlue]I WOULD EDIT IT LIKE SO[/COLOR]:

begin example:

```
[COLOR=Magenta][COLOR=Red]
[Desktop Entry]
Name=GQview
GenericName=Image Viewer
GenericName[et]=Piltide vaatur
GenericName[tr]=Resim göstericisi
GenericName[fr]=Explorateur d'images
GenericName[hu]=Képnéz&#337;
GenericName[es]=Visor de imágenes
Comment=View and manage images
Comment[hu]=Képek megjelenítése és rendszerezése
Comment[es]=Visualiza y administra imágenes
Exec=gqview -r %F
Icon=gqview.png
Type=Application
Terminal=false
# Startup notification disabled, since the remote -r switch may not open a new window...
#StartupNotify=false
#StartupWMClass=gqview
Encoding=UTF-8
Categories=Application;Graphics;Viewer;
MimeType=application/x-navi-animation;image/bmp;image/x-bmp;image/x-MS-bmp;image/gif;image/x-icon;image/jpeg;image/png;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-cmu-raster;image/x-sun-raster;image/x-tga;image/tiff;image/vnd.wap.wbmp;image/x-xbitmap;image/x-xpixmap;image/svg;image/svg+xml;image/x-png;image/xpm;image/x-ico;image/x-pcx[/COLOR];[/COLOR][COLOR=Magenta]
NoDisplay=true[/COLOR]

```</end example>

"If you don't have file monitoring support, run xfdesktop --reload to refresh the menu." -Xfce Wiki 

[COLOR=Blue]http://wiki.xfce.org/howto/customize-menu[/COLOR]

After that I would have to enter the following code into a terminal:

```
[COLOR=Magenta]
xfdesktop --reload
[/COLOR]
```OR

Press "[COLOR=Red]Alt+F2[/COLOR]" to bring up the Run dialog and enter:

```
[COLOR=Magenta]
xfdesktop --reload[/COLOR]

```HOPE this and the wiki link help you out. I am teaching myself this stuff this morning actually, so if you have further questions, please post or email me at: itsanudae at gmail dot com.

[COLOR=SeaGreen] GLAD[/COLOR] to help.

-Best, elliio

---

### Post by hikujk123 on 2008-04-19
Thanks.  I have a new install, so won't need this at the moment but I am sure I will many times in the future.

---

