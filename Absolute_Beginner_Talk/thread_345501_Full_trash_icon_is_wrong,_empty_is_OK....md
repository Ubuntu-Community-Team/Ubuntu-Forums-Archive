---
title: "Full trash icon is wrong, empty is OK..."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-01-24
Hi,

I have changed the icon theme and now the trash icon on the bottom panel (Gnome) reverts to the standard gnome icon when the trash is full. When empty the trash icon is the one of the theme I installed. Some icon themes work correctly but I'd like to fix the one I use. Is there anyway to rebuild the icon for the trash manually?? Where are the trash icons located?

Thanks

---

### Post by crossedout on 2007-01-24
Its likely that the theme you are using either doesn't have a "full trash" icon or it is simply named wrong within the theme.

Navigate to your home directory, press ctrl+h and navigate to .icons/<theme-name>
Look for an icon named: gnome-fs-trash-full.png or .svg (depending on your theme).  The trash icons are usually located in the 'filesystems' or 'places' sub-directories.  If it doesn't exist then you will need to import one from another theme or make your own.
If there is a trash-full icon, rename it to gnome-fs-trash-full.

Understand that if a theme does not come with an icon for a specific application etc., it will revert to the default icon theme unless otherwise modified.

-Xout

---

### Post by kilou on 2007-01-24
Thanks for the reply Crossedout. I checked in to the icon folder and there are several full trash icons named gnome-fs-trash-full.png corresponding to the various sizes of icons. So the full trash icons exists but they are just not used on the trash applet in the Gnome panel. Would this be a link problem???


EDIT: problem solved. I copied the full trash icon in the status folder of 128x128 and renamed it as user-trash-full.png and now it works. Thanks

---

### Post by liviubero on 2007-09-13
I also have two problems with the thrash can.

1. It doesn't want to show me when it is not empty, that is, it seems all the time empty. If I know that there are files in it and right click on it, then it doesn't give me the option "empty thrash" (or something like that), as it would be empty. I can delete the files in it by opening the thrash and than click on "empty thrash"

2.In the folder /home/<user>/.icons/<icons theme>/128x128/filesystems there are both files gnome-fs-trash-empty.png and gnome-fs-trash-full.png, but the thrash can won't show me the proper picture, but some other picture.

---

### Post by liviubero on 2007-09-13
I am trying to find out where does the thrash icon comes from...
I can't find it in the .icons folder, I can't find it in the /usr/share/pixmaps
Do you know where can I find this icon?
And perhaps is there any configuration file to modify?
Even if I change the icon theme, the thrash icon remains unchanged.

---

### Post by liviubero on 2007-09-14
Hi,
I just took a screen shot of what I mean. I should be obvious now.
1. Why does the thrash can shows the "empty" icon, if the thrash is NOT empty?

2.Why is there the false icon? You can see from the screen2.png that in my .icons folder there are the right ones... In theme.png you see that I how I set the icon theme... With other icon themes, it doesn't work also.

Any one any idea?

---

