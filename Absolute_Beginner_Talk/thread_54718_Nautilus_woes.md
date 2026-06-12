---
title: "Nautilus woes"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by OttoDestruct on 2005-08-05
Ok... I think the one thing I find I'm not happy about with Ubuntu is Nautilus. It's not 'bad', but I would prefer if I could get it to be *gasp* more like windows explorer. Only in the sense that I get a pane with where I'm working in the file tree, and another with  a list of my files. Is it possible to setup Nautilus to be like that, or do I have to use another program?

---

### Post by Reb on 2005-08-05
That side-panel treeview will be in Breezy I believe.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=OttoDestruct]Ok... I think the one thing I find I'm not happy about with Ubuntu is Nautilus. It's not 'bad', but I would prefer if I could get it to be *gasp* more like windows explorer. Only in the sense that I get a pane with where I'm working in the file tree, and another with  a list of my files. Is it possible to setup Nautilus to be like that, or do I have to use another program?[/QUOTE]


yes:

Put this in regular terminal:

> 
gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true

Sorry it took me a while to see this thread. This place is turning into a mad house- I'm having trouble keeping up

---

