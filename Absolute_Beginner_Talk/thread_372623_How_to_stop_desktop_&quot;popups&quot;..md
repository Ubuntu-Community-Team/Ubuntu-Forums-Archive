---
title: "How to stop desktop &quot;popups&quot;."
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by SumChipper on 2007-02-28
When I mouse over items on the desktop I get these little descriptions. I know in Windows you would change this in Folder Options but how do I do this in gnome?

---

### Post by charles.g.moore on 2007-02-28
> **SumChipper said:**
> When I mouse over items on the desktop I get these little descriptions. I know in Windows you would change this in Folder Options but how do I do this in gnome?

If you have gconf-editor or if not do: application > system tools> configuration editor
app>panel>global>uncheck tooltips

This only shuts off the panel tooltips...

I just did it and it seems to be kinda hit and miss, if you fid a better fix post it so I can use it too...

---

### Post by SumChipper on 2007-02-28
Synaptic shows that config editor is installed but it is not in the system tools tree. Any ideas?

---

### Post by Quillz on 2007-02-28
Did you start go into the Terminal and run ```
gconf
```?

---

### Post by mcduck on 2007-02-28
> **Quillz said:**
> Did you start go into the Terminal and run ```
gconf
```?

It's 'gconf-editor' ;)

---

### Post by SumChipper on 2007-02-28
Ahhh, I got it now. I was going through the Applications tree on the desktop and not gconf in terminal. 

Thanks for all your help!  /thumbs up/

---

