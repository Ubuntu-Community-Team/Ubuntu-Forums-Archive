---
title: "how do i switch kmenu icons?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-08-16
i'm using the black+white icon theme and i like the kmenu2 button better than the default for this theme. how can i switch them? for every other app, there is a right-click option to 'configure', including changing the icon.

---

### Post by ComplexNumber on 2006-08-16
> **fuscia said:**
> i'm using the black+white icon theme and i like the kmenu2 button better than the default for this theme. how can i switch them? for every other app, there is a right-click option to 'configure', including changing the icon.
are you talking about the actual main menu button thats usually denoted by a 'K' in kde? you will find that in the actual theme. in gnome, its called gnome-main-menu.png. i can't remember whats its called in kde, but it will be similar. you can always find it by choosing an icon theme with a destinctive main menu icon, then searching for it with in the icon theme.
or have i misunderstood completely? :p. its been awhile.

---

### Post by fuscia on 2006-08-16
> **ComplexNumber said:**
> are you talking about the actual main menu button thats usually denoted by a 'K' in kde? you will find that in the actual theme. in gnome, its called gnome-main-menu.png. i can't remember whats its called in kde, but it will be similar. you can always find it by choosing an icon theme with a destinctive main menu icon, then searching for it with in the icon theme.
or have i misunderstood completely? :p. its been awhile.

i'm just trying to use the kmenu2 icon instead of the kmenu icon. i ended up renaming the icons and let that do it, but, it seems like a gross way to do it. meh! it worked.

---

### Post by msak007 on 2006-08-16
If I understand correctly, you want to change the KMenu icon (the one you click on the launch the KMenu) to one that's not the theme default. That icon is located in **/home/<user name>/.kde/share/icons/<theme name>/<icon size>/apps**. You're looking for the file "kmenu.png". Simply rename that file for all the icon sizes (16x16, 32x32, etc.) to something like "kmenu_old.png" to back it up, then place the icon you want to use in the folder and name it "kmenu.png". Then go to System Settings / kcontrol and reload your theme to update it.

---

### Post by fuscia on 2006-08-17
> **msak007 said:**
> If I understand correctly, you want to change the KMenu icon (the one you click on the launch the KMenu) to one that's not the theme default. That icon is located in **/home/<user name>/.kde/share/icons/<theme name>/<icon size>/apps**. You're looking for the file "kmenu.png". Simply rename that file for all the icon sizes (16x16, 32x32, etc.) to something like "kmenu_old.png" to back it up, then place the icon you want to use in the folder and name it "kmenu.png". Then go to System Settings / kcontrol and reload your theme to update it.

that's what i ended up doing. it just seems to me that there should be a point and click solution to the problem (isn't that the point of using kde?).

---

### Post by msak007 on 2006-08-17
I agree that there should be some sort of function that lets you change the icon for the entire theme. I can't see how that would could be done easily though because you have all these different icon sizes, and maybe the icon you want to use only comes in 2 or 3 sizes. I had that problem when I wanted to change my KMenu and Trash Can icons, and ended up having to use imagemagick to convert the biggest icon size to some of the other icon sizes and manually backing up / renaming the files. It's not that hard, just a tedious process and confusing if you're not sure where to look. Maybe it can be added to the KDE4 wishlist.

---

