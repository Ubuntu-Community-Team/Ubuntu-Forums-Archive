---
title: "How to change &quot;open with&quot; in Thunar"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-12-31
I'm using Xubuntu 7.10 and I noticed that when I click on an image to open it in Thunar file manager it wants to open with thunderbird mail! this was set up by mistake. How do you change the "open with" to use a image program?

---

### Post by erfahren on 2007-12-31
right-click and "Properties" then it has a drop-down menu to change it

btw: I installed gThumb Image Viewer - I don't really like the GQview

---

### Post by fiddledd on 2007-12-31
Not 100% sure about this because I use gnome and nautilus, but if I remember right it's: Rightclick  the file select Settings -> Open with... and select the program you want to open it with.

---

### Post by fiddledd on 2007-12-31
i did it again, that's twice in as many days. Click Post Reply, type my answer, click Submit, then see someone else posted an answer 30 seconds before I clicked Submit :)

---

### Post by geovino on 2007-12-31
> **erfahren said:**
> right-click and "Properties" then it has a drop-down menu to change it

btw: I installed gThumb Image Viewer - I don't really like the GQview


Thanks, That worked! 

Also: Does anyone know how to add icons to the desktop or top pane in Xfce ?

---

### Post by erfahren on 2007-12-31
> **geovino said:**
> Thanks, That worked! 

Also: Does anyone know how to add icons to the desktop or top pane in Xfce ?
there is some documentation for that with xfce4 -

do this: right-click on the panel and "Add New Item" - scroll down to "Quicklauncher" and add it. The Quicklauncher (by default) sets four launchers together on the panel. 

One of those launchers is for the xfce4 documentation help file which goes into customizing the panel (among other things).

You can right-click on that same Quicklauncher then > Properties and add to or remove the individual launchers in it. 


there are some other applets that weren't installed by default that can be added to the panel, but are still available through the Synaptic Package Manager, you can see them under "Panel plugins" here: [http://goodies.xfce.org/](http://goodies.xfce.org/)

 -- one of them that I installed was the xfce4-datetime-plugin - it's better than the clock included with Xubuntu. You can search Synaptic for "xfce4" to see the packages (panel plugins, etc.) that are available.

That clock can be configured using the options from the [date command](http://www.linuxcommand.org/man_pages/date1.html) - mine is:
```

%a %b %d %l:%M %P

```

I have a screenshot of my current Xubuntu [attached to this post](http://ubuntuforums.org/showpost.php?p=4040437&postcount=1281) - if you want to see it.

I don't know about desktop launchers, but I hope that helped.

---

### Post by geovino on 2007-12-31
Thanks! I'll read up on it :)

---

