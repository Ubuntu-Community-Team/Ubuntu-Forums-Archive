---
title: "Resizing desktop icons in Gutsy"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by jkay on 2008-03-31
My desktop icons are all diffrent sizes, I searched this problem on google and most people went into nautlis and changed the zoom level but this did not work for me.  Does anyone know how to resize the desktop Icons to the same sizes?  If not do you know how to change desktop icons (I will probably just make all the icons default size 50x50.)  Thanks in advance.

---

### Post by scragar on 2008-03-31
you can just highlight them all, right click and choose restore orrigional size.

---

### Post by jkay on 2008-03-31
That button was greyed out but when I resized one of the icons It showed up.  Still didn't work.

---

### Post by jkay on 2008-04-01
bump

---

### Post by Trevms on 2008-04-01
Right click on the desktop icon and select the "Stretch Icon" menu option.  Click hold and drag one of the corner squares to resize the icon.

---

### Post by jkay on 2008-04-02
Sorry, I forgot to mention that I already know how to do that.  I want all the icons to be the same size and any new icons to be the same.  This seems to be somewhat hard to do, so does anyone know how to edit the icon file?  I usually keep the same 10 icons on my desktop so I could just open the original icon file and make it bigger/smaller.

---

### Post by jkay on 2008-04-03
Nobody knows how to change icon files or resize multiple icons?

---

### Post by Xiong Chiamiov on 2008-04-03
I don't know where the icons are in gnome, but I'm pretty sure you can edit them in GIMP.

---

### Post by mrboojive on 2008-04-03
Some of the icons are vector graphics (.svg) and some are raster graphics (.png or something). The ones that are .png, Firefox is one example, show up on your desktop as whatever dimensions the .png file has and not the default icon size.
You can always find the .png file that is used for the icon in /usr/share/pixmaps, copy it somewhere, resize it to the size of your other icons and then set the resized image as your icon. Alternatively, you could actually resize the file in /usr/share/pixmaps using administrator privileges, but that's probably not such a good idea.
Hardy doesn't have this problem, it displays all icons as the same size, seems to be a fix in the new version of Gnome. So if you're going to upgrade when Hardy comes out, you can just wait for a couple weeks.

---

### Post by dilney on 2008-04-03
I think nobody really understood your problem.

By default, all icons are the same size and small.  You know how to make them bigger (one by one), but you would like Gnome to make all bigger and the same size.

Unfortunately, I don't know the answer, but would also appreciate if someone more knowledgeable could help us.

Thanks.

---

### Post by mrboojive on 2008-04-03
> By default, all icons are the same size and small. You know how to make them bigger (one by one), but you would like Gnome to make all bigger and the same size.
The size of icons on the desktop is the same as the size of icons in Nautilus, the file manager. You can change it by going to Edit > Preferences in Nautilus.

---

