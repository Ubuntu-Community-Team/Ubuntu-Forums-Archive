---
title: "editing xorg.conf"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by davesbrain on 2008-01-31
Strange...When I try and edit xorg.conf with sudo gedit /etc/X11/xorg.conf, the editor opens with only a xorg.conf tab at the top and nothing else, empty.  When I use the root terminal with just gedit /etc/X11/xorg.conf...same thing, blank with just the tab up top.

When I actually 'browse' to it and double click it to just view it...all there.

The nano command in regular terminal works fine.

Could someone please explain this.

---

### Post by philinux on 2008-01-31
I had this when I forgot the capital X.

If you use x11 then gedit just creates a blank document.

---

### Post by ayenack on 2008-01-31
If its not the "X" then try gksu rather than sudo.

gksu gedit /etc/X11/xorg.conf

Sometimes there can be issues with permissions when using sudo with a graphical application.

---

### Post by LowSky on 2008-01-31
> **davesbrain said:**
> Strange...When I try and edit xorg.conf with sudo gedit /etc/X11/xorg.conf, the editor opens with only a xorg.conf tab at the top and nothing else, empty.  When I use the root terminal with just gedit /etc/X11/xorg.conf...same thing, blank with just the tab up top.

When I actually 'browse' to it and double click it to just view it...all there.

The nano command in regular terminal works fine.

Could someone please explain this.

I have actually had the same issue...odd, but I was forgetting to put '/' before 'etc/'

make sure your code is correct

```
 sudo gedit /etc/X11/xorg.conf
```

try this as well

```
 gksu gedit /etc/X11/xorg.conf
```

---

### Post by davesbrain on 2008-01-31
OH jeesh.   Silly me.   I was not putting the slash before the etc.   (Homer..."Doh!")

Is there a preferred method to edit sensitive files?   Nano reminds me of old Xtree Gold for windows.....very powerful and capable of making powerful mistakes.   I kind of prefer using an editor.

PS....I just had to disable the compositing to try and get Maya to work.  It didn't so I re-enabled the compositing.  Think I'll hold off on that for a while.

---

### Post by ayenack on 2008-02-01
> **davesbrain said:**
> 
Is there a preferred method to edit sensitive files?   Nano reminds me of old Xtree Gold for windows.....very powerful and capable of making powerful mistakes.   I kind of prefer using an editor.

Most people just use gedit or nano. I would suggest using gksu or gksudo instead of sudo when using gedit to edit a file. In nano you can use straight old sudo with no problems at all.

---

