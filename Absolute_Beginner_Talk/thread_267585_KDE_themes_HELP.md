---
title: "KDE themes? HELP"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-09-28
How do I change my theme for KDE???

I can't figure it out!

---

### Post by Kateikyoushi on 2006-09-28
System settings  >> appearence.

There is also a theme manager for KDE.

[Get themes here]("http://www.kde-look.org/").

---

### Post by kbsuperstar on 2006-09-28
How do I get the theme manager?

---

### Post by Kateikyoushi on 2006-09-28
sudo aptitude update
sudo aptitude install kdmtheme

---

### Post by kbsuperstar on 2006-09-28
So, how do I run it after I install it?

---

### Post by Kateikyoushi on 2006-09-28
Should be somwhere in the menu I can not tell exactly because I am not on gnome but if you can't find it type in the terminal: kdmtheme

---

### Post by ewl1217 on 2006-09-28
Kdmtheme is to change the theme of the login manager. To change your KDE theme, run kcontrol at the terminal, since it has a theme manager in it. You can create a menu entry for kcontrol if you want.

---

### Post by kbsuperstar on 2006-09-28
Ok... 

I ran kcontrol, but it says the theme I want to install isn't a theme file. It's a .tar.bz2


?

---

### Post by ewl1217 on 2006-09-28
Try extracting the .tar.bz2 file using ark, or another archive tool. The theme file might just have been packed inside it.

---

### Post by Kateikyoushi on 2006-09-28
> **ewl1217 said:**
> Kdmtheme is to change the theme of the login manager. To change your KDE theme, run kcontrol at the terminal, since it has a theme manager in it. You can create a menu entry for kcontrol if you want.

Really ? Sorry. ](*,) 

That's what I found in synaptic, might have misunderstand something.:-# 

```
theme manager for KDM
kdmtheme is a theme manager for KDM. It provides a KDE Control Module (KCM)
that allows you to easily install, remove and change your KDM themes.

```

---

### Post by kbsuperstar on 2006-09-28
Umm?[IMG]http://xs107.xs.to/xs107/06395/snapshot1.png[/IMG]

---

### Post by ewl1217 on 2006-09-28
Are you sure that's a KDE theme? One of the folders in there seems to be for IceWM...

**EDIT:** Just as an afterthought, you should probably read the README that come in the archive.

---

