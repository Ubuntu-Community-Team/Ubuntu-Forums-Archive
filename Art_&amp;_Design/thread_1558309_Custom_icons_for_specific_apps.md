---
title: "Custom icons for specific apps"
date: 2010-08-22
forum: Art &amp; Design
---

### Post by TheWeakSleep on 2010-08-22
I wasn't entirely sure where to ask this, but I would like to make custom icon sets for the GIMP and OpenOffice.org. Is it possible to change the default icons?

any help would be appreciated, and feel free to move this to a more appropriate place if necessary :D

---

### Post by sikander3786 on 2010-08-22
If you want custom icon sets, [Icon Theme]("http://gnome-look.org/index.php?xcontentmode=120x121&PHPSESSID=0788f18c986f839813b5958ba35ff448") is the best way to start with.



However individually it is possible but not without a hassle I believe (I haven't tried) e.g, GIMP has it icon in /usr/share/gimp/2.0/images.

---

### Post by TheWeakSleep on 2010-08-22
Thank you for the help, the reason i am asking is that the icon theme i am using, (a few from ACYL, ubuntu-mono-dark, moblin, some custom made, and some other miscellanous ones) makes the icons used by GIMP and openoffice.org look completely out of place, and i would like to change them. Thanks for pointing to where GIMP's icons come from, do you or anyone else know where openoffice.org's are? thanks in advance.

---

### Post by sikander3786 on 2010-08-22
For OpenOffice there's already a thread.

[http://ubuntuforums.org/showthread.php?t=230286&page=2](http://ubuntuforums.org/showthread.php?t=230286&page=2)

---

### Post by TheWeakSleep on 2010-08-22
I suppose i should have clarified a bit more. I'm not looking to change the icon OF the application. I'm looking to change the icons IN the application. 

For instance, the toolbar icons in openoffice.org and the tool icons in gimp.

---

### Post by durand on 2010-08-22
I know that inkscape has an svg in its installation folder which contains all its interface icons,  the gimp might be similar. I'm on my phone now so I can't check but try looking in /usr/share/inkscape. You will then need to copy over your set of icons with root access.

---

### Post by TheWeakSleep on 2010-08-22
Thanks for your help durand! It took some digging but I found where the icons are hiding for gimp :) openoffice.org seems like it'll be a little harder though! I can't find anything relevant. any ideas!?

---

### Post by chips24 on 2010-08-22
well, another thing you could do. You could go into the menu editor by right-clicking on your main menu or menu bar, click on edit menus, right click on the application icon, click on properties, than click on the icon picture on the launcher properties to upload a custom picture that you want to use for the application. You can also do the same with desktop and folder icons.

---

### Post by durand on 2010-08-23
> **chips24 said:**
> well, another thing you could do. You could go into the menu editor by right-clicking on your main menu or menu bar, click on edit menus, right click on the application icon, click on properties, than click on the icon picture on the launcher properties to upload a custom picture that you want to use for the application. You can also do the same with desktop and folder icons.

The OP means toolbar icons.


And sorry, I misread your post as wanting to change inkscape icons. I think openoffice may be in /usr/share/pixmaps.

---

### Post by TheWeakSleep on 2010-08-23
Thanks durand you're a lot of help :D
And no worries about the inkscape thing, if I'm making custom sets for gimp and oo.o..
why not inkscape too? ;)

EDIT: I took a look in /usr/share/pixmaps/ and couldn't find any reference to openoffice.org.

I have also looked in /usr/lib/openoffice/ and I can't find anything to do with where these icons come from!

In the repos there are a few packages that start with openoffice.org-style-
These are icon sets for openoffice.org (Human, Tango, etc.)
but i would still like to know how to make a custom one?

---

