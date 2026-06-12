---
title: "how to change edgy main menu?"
date: 2006-12-14
forum: Art &amp; Design
---

### Post by joplass on 2006-12-14
i would like to change edgy main menu icon to the gnome foot.  i have tried a few dapper threads with no luck ](*,) .
anyone please!

---

### Post by bapoumba on 2006-12-15
Hi,
should be /usr/share/icons/Human/48x48/places/start-here.png.
I have not tried changing it ;)

---

### Post by hikaricore on 2006-12-15
Also you may need to restart gnome-panel for this to take effect:

```
killall gnome-panel
```

After you replace the image will restart it :)

---

### Post by joplass on 2006-12-16
thanks fellas but it did not work for me.  all ubuntu icons in folder /places changed to the gnome foot but the main-menu icon is still ubuntu.

---

### Post by bapoumba on 2006-12-16
[http://www.ubuntuforums.org/showthread.php?t=314767]("http://www.ubuntuforums.org/showthread.php?t=314767")
Would this help ?

---

### Post by joplass on 2006-12-16
nice thread there...it worked like a charm. 
thank you,

---

### Post by adrianus on 2006-12-22
Using information in
[http://www.ubuntuforums.org/showthread.php?t=314767](http://www.ubuntuforums.org/showthread.php?t=314767)
The changes only applies to that particular instance of object.
If you delete the main menu from the panel and re-add the object, it will again use the default ubuntu-logo

I find out that actually there are several files that is used depend on the panel size (if you are using Human icon theme)
change these files and the changes will affect system-wide (all user using that theme)


/usr/share/icons/Human/scalable/places/start-here.svg
/usr/share/icons/Human/48x48/places/start-here.png
/usr/share/icons/Human/24x24/places/start-here.png

If the icon theme you are using currently doesn't have the icon for main menu, the icon that will be used is the icon :
/usr/share/icons/gnome/scalable/places/start-here.svg

Hope this information helps.

---

### Post by adrianus on 2006-12-24
Additional info : the information I post above work on Ubuntu Edgy 6.10
Here's what I did to make the changes also applied to menu bar, not just main menu, I first switch to other theme icon, then I edit the theme file for Human icon theme.
It is located in /usr/share/icons/Human and the name is index.theme
I remove the inheritance to Tango and Tangerine, (keep the inheritance to gnome theme) then switch back to Human icon theme.
Then I decided to undo the changes and re-edit the index.theme file (switch to other theme first before doing the editing) to restore inheritance to Tango and Tangerine theme, but the modified icon is still showing.
I guess the act of editing the index.theme and switching to other theme somehow reset the cache for icons.

---

