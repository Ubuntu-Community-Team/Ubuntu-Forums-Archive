---
title: "[SOLVED] missing menu bar"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by NateMan on 2008-02-08
My top menubar disappeared on my ubuntu installation, however I don't have another menu bar to right click on and regain it. I can't figure out where to go to get another menu bar and any help would be greatly appreciated.

---

### Post by nynoah on 2008-02-08
just wondering how you lost it?

either way, I hope you still have at least on panel.  if you do, hover over that and R click.  The hit "new panel"  That will give you a new one.  The right click on your new panel and hit "add to panel" to add the things you want.  Have fun customizing.

---

### Post by nikoPSK on 2008-02-08
> **NateMan said:**
> My top menubar disappeared on my ubuntu installation, however I don't have another menu bar to right click on and regain it. I can't figure out where to go to get another menu bar and any help would be greatly appreciated.
 
it's a "panel". Goto your bottom one, right click then add new panel. Add the appropraite applets. :)

---

### Post by NateMan on 2008-02-09
Ok its a "panel" and I was only using one "panel". I changed a configuration option on my panel and it disappeared and will not come back with a restart. Does anyone know how to get it back? I do NOT have another panel to right click on.

---

### Post by nikoPSK on 2008-02-09
> **NateMan said:**
> Ok its a "panel" and I was only using one "panel". I changed a configuration option on my panel and it disappeared and will not come back with a restart. Does anyone know how to get it back? I do NOT have another panel to right click on.

okay, to your bottom panel, right click it (the blank whitish part) click new panel. Drag the new blank panel to the top. Right click now, add to panel.

Add the quit applet at the right, volume control to it's left, network monitor to *it's *left, notification area and then user switcher. On the left of the panel, add the Menu bar applet.

EDIT: oops misunderstood :oops:

---

### Post by badmedic on 2008-02-09
What happens if you press Alt F2 to get the run dialog and then type in "gnome-panel" and run it?

I am not sure it will work, but I think it might!

---

### Post by NateMan on 2008-02-09
I tried the alt +F2 and then running "gnome-panel" but no help there either. I think something may have occured that totally fried my panel. Any body else have any ideas?

---

### Post by badmedic on 2008-02-09
Hmmm... according to the Gnome Panel help, you cannot delete a panel when it is the only one you have. Are you sure you didnt turn on the panel's autohide option? Have you tried running your mouse all around the edge of your screen?

---

### Post by badmedic on 2008-02-09
Also, take a look at [http://ubuntuforums.org/showthread.php?t=539513](http://ubuntuforums.org/showthread.php?t=539513) if autohide is not the issue. Hope this helps!

---

### Post by nikoPSK on 2008-02-09
> **badmedic said:**
> Hmmm... according to the Gnome Panel help, you cannot delete a panel when it is the only one you have. Are you sure you didnt turn on the panel's autohide option? Have you tried running your mouse all around the edge of your screen?

just a question, id you accidentally delete the menu? Or did it randomly disappear?

---

### Post by jan quark on 2008-02-09
and what happens if you run


```
metacity --replace
```

---

### Post by NateMan on 2008-02-09
metacity --replace worked! My panel came right back and I was able to get it fixed by changing some settings. Thank you very much!

---

### Post by nikoPSK on 2008-02-09
> **NateMan said:**
> metacity --replace worked! My panel came right back and I was able to get it fixed by changing some settings. Thank you very much!

please mark this thread as solved in thread tools. :)

---

### Post by buntu_Geek on 2008-02-09
...

---

### Post by buntu_Geek on 2008-02-09
There is a possibility to delete the panel...

Anyway if you are sure that you didnt delete the panel...then you might have increased the transparency (try putting a white desktop wallpaper to recognize the panel...)

---

### Post by nikoPSK on 2008-02-09
> **buntu_Geek said:**
> There are options to delete a panel....
but if your sure that you didn't delete it.... you might have increased the transparency of your panel, or auto hided it....

Yes, transparency still makes it visible. 

> **buntu_Geek said:**
> There is a possibility to delete the panel...

Anyway if you are sure that you didnt delete the panel...then you might have increased the transparency (try putting a white desktop wallpaper to recognize the panel...)

pretty sure he got it. :)

---

