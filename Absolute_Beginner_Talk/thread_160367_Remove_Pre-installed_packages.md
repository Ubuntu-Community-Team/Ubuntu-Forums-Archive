---
title: "Remove Pre-installed packages"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2006-04-14
Hey,

Im trying to remove some packages from my install but in synaptics when i check remove. it wants to also remove the ubuntu-desktop. How can i remove these files without having to remove my desktop? I want to tweak the preformance of my laptop and would like to free up the space aswell. Well now im off to speed up my boot process.. 

Thanks
~Lance

---

### Post by gingermark on 2006-04-14
ubuntu-desktop is a metapackage, and can be removed safely. Metapackages are used to easily install several packages. For example, I am a KDE user, but if I wanted to use GNOME I could install ubuntu-desktop and I would get all the packages that consists of. But then if I removed one, not all the packages that ubuntu-desktop consists of would be installed anymore, so ubuntu-desktop is removed.

I would advise you to re-install ubuntu-desktop before upgrading to Dapper though, as THAT ubuntu-desktop will most likely consist of different packages.

---

