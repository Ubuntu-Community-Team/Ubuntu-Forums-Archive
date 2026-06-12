---
title: "Questions/Problems with Kmenu and Kmenu editor"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-27
Hi I have installed the kubuntu-desktop package with aptitude over gnome, and I log into a kde session, but the default applications for kde are not there,  just all of my gnome applications and a few kde applications.  i think this is caused by the one time when i installed the kubuntu-desktop and then i removed some kde programs from the kmenu but then i uninstalled the kubuntu-desktop package.  that was a while ago thouugh.  i did it again, but apparently some config file was left over for the kmenu.  so basically how do i get the default applications back in my kmenu?  (i don't like the kmenu editor, it doesn't let you hide applications, only remove them from the list!!)

---

### Post by henriet on 2006-06-27
Hello,
try to have a look there:
[http://docs.kde.org/development/en/kdebase/userguide/kde-menu.html](http://docs.kde.org/development/en/kdebase/userguide/kde-menu.html)

---

### Post by aysiu on 2006-06-27
You could try ```
mv ~/.kde ~/.kde.old
killall kicker
kicker
```

---

### Post by user1397 on 2006-06-27
[quote=aysiu]You could try ```
mv ~/.kde ~/.kde.old
killall kicker
kicker
```[/quote]that only restarted the panel, not the kmenu. good try though, thanks.

---

### Post by aysiu on 2006-06-27
Well, try logging out and logging back in again. I don't know how to refresh the KMenu manually.

---

### Post by user1397 on 2006-06-27
[quote=aysiu]Well, try logging out and logging back in again. I don't know how to refresh the KMenu manually.[/quote]nope, logging out and back in didn't work either.

---

### Post by aysiu on 2006-06-27
How about this? ```
mv ~/.config/menus/applications-kmenuedit.menu ~/.config/menus/applications-kmenuedit.menu.old
kbuildsycoca --noincremental
```

---

### Post by user1397 on 2006-06-27
[quote=aysiu]How about this? ```
mv ~/.config/menus/applications-kmenuedit.menu ~/.config/menus/applications-kmenuedit.menu.old
kbuildsycoca --noincremental
```[/quote]yep, that just about did it! how did you find that out so fast?! basically, my kmenu is filled with every gnome/kde app possible, but i want to try to make it so that the best of gnome and best of kde are fused together into one super menu.

---

### Post by aysiu on 2006-06-27
[QUOTE=erik1397]how did you find that out so fast?![/QUOTE] When you spend a lot of time helping others on the forums, you learn to Google really well.

I don't have most of the problems other people have, so I don't know how to solve these problems myself. I have to figure it out with them. So this I solved with a Google search for: ```
site:kde.org restore default kmenu
```

---

### Post by user1397 on 2006-06-27
[quote=aysiu]When you spend a lot of time helping others on the forums, you learn to Google really well.

I don't have most of the problems other people have, so I don't know how to solve these problems myself. I have to figure it out with them. So this I solved with a Google search for: ```
site:kde.org restore default kmenu
```[/quote]ah I see, I gotta learn how to google like that...:-k

---

