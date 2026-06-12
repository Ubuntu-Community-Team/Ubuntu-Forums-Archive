---
title: "xgl at dapper 606 - themes don't work"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by elnino on 2006-07-12
hi!

I've recently installed ubuntu606 in my desktop, and xgl as well... but I can't install any theme.

I do the download from gnome-look.org (gmd themes section), and I drop the file in the theme manager and press "install", but it says that the file is invalid or it can't read it well! ](*,)

could you help me out here, plz?

(sorry 4 the bad english... not my mother language:-# )

---

### Post by givré on 2006-07-12
Some theme gnome-look.org are not package the way it should be.
The majority of the time, it's because this package contain several theme. Unpack the first one and you should have several package that you will be able to drag&drop.
If it's not work, what is the specific theme you want to install.

---

### Post by Miguel on 2006-07-12
Good evening!

Well, it seems to me you are installing a gdm theme like you would a normal gnome theme. GDM themes work a bit differently, because they are stored in a place in your computer where only the admin (root) can write to. Let's try the following:[list]
[*]Click on System -> Administration -> Login screen (or similar). 
[*]It will ask for your password. Go ahead.
[*]Drag and drop the theme file to the box showing you the different themes. 
[*]Accept to install the new theme and select it from the list
[/list]

Please note that a GDM theme is the screen and button you see after the boot process has finished. My current GDM theme is this:
[http://www.gnome-look.org/content/show.php?content=37395](http://www.gnome-look.org/content/show.php?content=37395)

Hope it helps ;)

*EDIT:* You won't be able to change the window bar in Xgl, because compiz uses his own.

---

### Post by elnino on 2006-07-12
> **givré said:**
> Some theme gnome-look.org are not package the way it should be.
The majority of the time, it's because this package contain several theme. Unpack the first one and you should have several package that you will be able to drag&drop.
If it's not work, what is the specific theme you want to install.

in fact that was part of the problem... that way the theme is installed, but nothing change when I select it...

reboot maybe?

---

### Post by KFASheldon on 2006-07-12
Hi - Noticed you have installed xgl, and am I safe to asume compiz as well, so you can have all those wonderul openGL wobbly windows and the cube.  

If that is the case then sorry GDM Themes wont affect min,max, close widgets on your windows only things you will change ore the sliders and buttons and such within windows and poss the frame a little.  

If you are using compiz-quinn then you should have a preferences compiz themes icon, this will allow you to chage colours and transparency of window borders but sadly not the widgets.  Also dont be misled by GsetCompiz and the decorator plugin as I initialy was - searched everyplace for the conrol for the winodw decorations, Errr!

Does anyone know if work on a true theme engine for compiz is on its way so we can get our widgets back - the installed one are not the best and I would realy like my mac style back with compiz - thanks

---

### Post by KFASheldon on 2006-07-17
Widget themes support seams to have been sneeked into Compiz Themer now, all that is needed now is some active theme repository. Now I can have my wdets back. Thanks

---

### Post by adam.tropics on 2006-07-17
And worth a mention is that whilst the new theming stuff in Compiz is great, what gnome (metacity) theme you are using still effects things like the panel and menus. The effect Compiz currently has on panel and menus is limited to things like (not esclusively) opacity.

---

