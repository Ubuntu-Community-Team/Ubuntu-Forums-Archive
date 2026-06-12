---
title: "Icons"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-06
I have TONS of icons in the .ico .png formats
how do I install them ?
cuz in the Emblems I can see just a very limited number of icons 
BTW can I set .ico icons or just .png ?

---

### Post by Dr. Nick on 2006-07-06
was this a icon set you download, or just pictures you got and want to use as icons?

Then emblems section is different, you can add emblems to a certain file/folder to make it stand out some.

If you are just looking to change a few program icons with various pictures not from a icon set then just

Right click the current icon, hit properties then click the icon by the name field and you can navigate to the picture you want.

If its a icon set for gnome from a website the look at System - Preferences - Themes

---

### Post by Al3xanR0 on 2006-07-06
[QUOTE=MAXDDARK]I have TONS of icons in the .ico .png formats
how do I install them ?
cuz in the Emblems I can see just a very limited number of icons 
BTW can I set .ico icons or just .png ?[/QUOTE]

As far as I know GNU/Linux will use .png files as icons, however, .ico is a M$ extention. Nevertheless, they can be converted to .png files which are supported byGNU/Linux natively. I am not quite sure what utility can be used in Gnome to perform this action, but in KDE you can use "kiconedit"

kiconedit is an icon editor for KDE
KIconedit allows you easily to create and edit icons.

This package is part of KDE, as a component of the KDE graphics module.
See the 'kde' and 'kdegraphics' packages for more information.

Installing it is as easy as typing in the following

```
sudo apt-get install kiconedit
```

---

### Post by c1ean on 2006-07-06
Is there any way to take .png's and convert them into an Icon Theme, similar to Iconpackager for Windows?

---

### Post by MaximB on 2006-07-06
I have gnome desktop...will kiconedit work ??? (don't like the windows style menu - I just got rid of this carp (winxp))
it is in fact a huge 2-3 GB rar file with amount of .ico and .png files I can't even count :)
how can I make thouse icons apear in the emblem ?

---

### Post by Frank Golden on 2006-07-06
[QUOTE=MAXDDARK]I have gnome desktop...will kiconedit work ??? (don't like the windows style menu - I just got rid of this carp (winxp))
it is in fact a huge 2-3 GB rar file with amount of .ico and .png files I can't even count :)
how can I make thouse icons apear in the emblem ?[/QUOTE]
A lot of icons are located in /usr/share/pixmaps. I know there is a more elegant way to add icons to this file but I just use the "gksudo nautilus"
command to allow me temporary permission to add icons. As far as changing
.ico to .png all I do is change name from xxx.ico to xxx.png, seems to work for me. Don't even know what emblems are but in an icon property box,
if you click on the icon symbol you will be able to change icon or browse
to folders where you can find other icons. Many system icons are at /user/share/pixmaps.

---

