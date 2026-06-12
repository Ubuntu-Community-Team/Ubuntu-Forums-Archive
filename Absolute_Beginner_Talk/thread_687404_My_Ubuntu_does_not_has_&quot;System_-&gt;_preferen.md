---
title: "My Ubuntu does not has &quot;System -&gt; preferences -&gt; themes&quot; ?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-04
Hi
I have Ubuntu 7.10 and in many tutorial I saw that I need to install icons using the System -> preferences -> themes application, but it is not present in my installation, what should I do?

thanks

---

### Post by PmDematagoda on 2008-02-04
The Themes application has moved to System>Preferences>Appearance. Just thought you might want to know:).

---

### Post by jan quark on 2008-02-04
system > preferences > appearance > themes

---

### Post by y-lee on 2008-02-04
Let's see if it is installed try the below in a terminal.:

```
gnome-theme-manager
```

and let me know if this opens the theme manager up.

If so it is probably either not checked in your menu or has been some how deleted from your menu,  to check start Alacarte Menu Editor, look for it in your menu under accessories or type in the terminal.

```
alacarte
``` 

see if **theme ** is present and checked under preferences. 

If theme is not there post back we will add an entry for it, or if you know how go ahead and do it. Let us know :)

---

### Post by legolas_w on 2008-02-04
Hi
Thank you for reply.
But I can not find how I can install icons, I copied some icons in ~/.icons/icons_gusty_ubuntu/ but I do not know how i cam make the linux use them.
The readme file which was supplied with Icon pack said that in Open theme manager and then use that icon pack.


Thanks

---

### Post by forestpixie on 2008-02-04
generally you open the theme manager and drag the icon tar file into it and it will install for you - or once the manager is open use the install button and navigate to your folder

afaik you do not need to unpack the package

---

### Post by Pandemic187 on 2008-02-04
> **legolas_w said:**
> Hi
Thank you for reply.
But I can not find how I can install icons, I copied some icons in ~/.icons/icons_gusty_ubuntu/ but I do not know how i cam make the linux use them.
The readme file which was supplied with Icon pack said that in Open theme manager and then use that icon pack.


Thanks
If this is done manually they should be moved to the /home/(user)/.icons folder (Is that the same as ~/.icons? If so, I would think that what you did should work).

However, this can be done through the GUI in 7.10 (assuming the theme is indexed) by going to System>Preferences>Appearance>Themes. When your current theme system is selected, click the "Customize..." button, where you'll find a tab for icons. Drag the icon theme there and you should be able to use it. Indeed this way doing it is it a bit confusing, but once you know how to do it, it's not so bad.

---

### Post by forestpixie on 2008-02-04
you can just drag the icon package onto the theme manager without going as far as the customise/icon thing

---

