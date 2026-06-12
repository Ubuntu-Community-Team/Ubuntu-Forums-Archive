---
title: "Update error message?"
date: 2005-09-23
forum: Bug Reports / Support
---

### Post by wizzer on 2005-09-23
So far I have been able to install all updates but one?  x common version 1.08.  This is the error message it gives me.  Any help with this would be greatly appreciated 

 :roll: 
E: /var/cache/apt/archives/x-common_1.08_all.deb: trying to overwrite `/usr/lib/X11/fonts', which is also in package xfonts-base

Thanks so much!
wizzer

---

### Post by serzz on 2005-09-24
[QUOTE=wizzer]So far I have been able to install all updates but one?  x common version 1.08.  This is the error message it gives me.  Any help with this would be greatly appreciated 

 :roll: 
E: /var/cache/apt/archives/x-common_1.08_all.deb: trying to overwrite `/usr/lib/X11/fonts', which is also in package xfonts-base

Thanks so much!
wizzer[/QUOTE]
 Had this problem too. I've just removed with synaptic packages named: xfonts-100dpi, xfonts-75dpi, xfonts-base, xfonts-scalable and x-window-system-core. Then I've runed update and after that installed all packages I removed before.

---

