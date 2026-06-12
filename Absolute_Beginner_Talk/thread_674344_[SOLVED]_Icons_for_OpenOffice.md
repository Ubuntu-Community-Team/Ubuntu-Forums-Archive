---
title: "[SOLVED] Icons for OpenOffice"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Ohwii on 2008-01-21
Hi guys,

I need some help changing the icons of the Open Office files. I mean I am using AWN Manager and every time I am opening a openoffice file the icons on the bar is quite 'blurry'.
Also I want to change the global icon of Openoffice files in nautilus. 

I tried to install some themes and icons from some gnome pages but they always stay the same. 

So would be very nice if someone could help me out changing the file icons of open office files. 

OhWii

PS:

I am using 
* Ubuntu 7.10 gusty 
* gnome 2.20.1

---

### Post by Perfect Storm on 2008-01-21
Is it OOs application launcher?

Then you need to change/add these in your ./icons/<theme>/<size>/apps

ooo-base.png     ooo-math.png          openofficeorg-base.png
ooo_calc.png     ooo.png               openofficeorg-calc.png
ooo-calc.png     ooo_printeradmin.png  openofficeorg-draw.png
ooo_draw.png     ooo-printeradmin.png  openofficeorg-impress.png
ooo-draw.png     ooo_template.png      openofficeorg-math.png
ooo_gulls.png    ooo_web.png           openofficeorg.png
ooo_impress.png  ooo-web.png           openofficeorg-printeradmin.png
ooo-impress.png  ooo_writer.png        openofficeorg-web.png
ooo_math.png     ooo-writer.png        openofficeorg-writer.png

in every size.

---

### Post by frup on 2008-01-21
I don't know about AWN but for a standard launched you click on properties and then click the icon in the dialogue and then change the icon from there.

You can do this with say a .odt file as well... I'm not sure if this is system wide or just for the individual file though (i haven't bothered to check)

The contents of folders like /usr/share/pixmaps might interest you... if you can locate the icons being called you can replace them with an alternate image.

---

### Post by Ohwii on 2008-01-21
First of all thanks for the fast reply. 

but I do not understand the 'is OOs application launcher?' AI ( if I may call you that)
If I understand it correctly it is the icon in the application tablete-> office. But I also want to change the icons of global .odt, .ods - files .    

Therefore I want to change both. 

In addition, to frup's post: it is just a individual change not a global one, therefore it would be kind of long to do it with every file.;)

by the way AI. is there an other way to change the icons in the .icon/(theme) folder. because there are quite much (24*24; 48*48; scale able etc.)? [ is it usr/share/icons ? I am a absolute beginner!:-P]


Thanks again for the quick help. =D>

Ohwii

---

### Post by Perfect Storm on 2008-01-22
Well, it's the same in usr/share/icons regarding size.

The .odt etc. files are
in the mimetypes folder of the theme


Better would be downloading and installing a theme who already made the changes. Try with blendedcrystal it does that.

[http://gnome-look.org/content/show.php/Blended+Crystal?content=58001](http://gnome-look.org/content/show.php/Blended+Crystal?content=58001)

---

