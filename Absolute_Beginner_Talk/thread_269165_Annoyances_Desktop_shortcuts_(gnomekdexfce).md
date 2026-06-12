---
title: "Annoyances: Desktop shortcuts (gnome/kde/xfce)"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-10-01
**[SIZE="4"]Desktop Icons in Gnome (Ubuntu):[/SIZE]**
[SIZE="3"]_Home Directory_[/SIZE]
```
$ *gconf-editor*
Apps > Nautlius > Desktop > "home_icon_visible" checked
```
[SIZE="3"]_Trash_[/SIZE]
```
$ *gconf-editor*
Apps > Nautlius > Desktop > "trash_icon_visible" checked
```

**[SIZE="4"]Desktop Icons in KDE (Kubuntu):[/SIZE]**
[SIZE="3"]_Home Directory_[/SIZE]
```
1) Open Konqueror
2) Surf to /home
3) Find user's folder (ie: /home/altonbr/)
4) Drag onto desktop
5) Click "Link here" in the menu that pops up
```
[SIZE="3"]_Trash_[/SIZE]
```
$ *gedit kate ~/Desktop/trash.desktop*

paste:
[Desktop Entry]
Comment=Contains removed files
Encoding=UTF-8
Icon=trashcan_full
EmptyIcon=trashcan_empty
Name=Trash
Type=Link
URL=trash:/

```

**[SIZE="4"]Desktop Icons in Xfce (Xubuntu):[/SIZE]**
[SIZE="3"]_Home Directory_[/SIZE]
```
???
```
[SIZE="3"]_Trash_[/SIZE]
```
???
```

I read you can add icons if you install Nautlius of Thunar... but I rather have this install be as clean as possible since it's on my Nephews old Pentium III (P3) laptop.

Also, I can probably just create a .desktop file and place the correct settings in it for the home and trash icons to appear.

So how should I go about this?

I would also just like to point out that I find it silly to have to many ways to do one thing when it SHOULD be done all one way. Desktop icons should be an intristic part of any theme, just like the desktop is across Mac OS X, Windows 95-Vista and Gnome/KDE/Xfce/etc.

Gnome and KDE have it correct to right-click a program in the menu and have a "Add to Desktop" option for shortcuts... but it's not the same for the home and trash directories... those you have to search the forum for. 

In Windows XP, you right click on the desktop, select properties, click the Desktop tab, and click something about Desktop Icons (so you can add icons that are parallel to the home directory). The trash (recycle bin) icon is default.

Maybe this will be improved in 6.10 (Edgy)??

Anyway, sorry for the rant, but does anyone know how to do the following in Xfce:

-program shortcuts
-trash can
-home directory

Or should I create those .desktop files and someone will give me the correct settings to use.

---

### Post by SoliTear on 2006-10-27
I agree also, making desktop shortcuts should be a normal task as well.

---

### Post by altonbr on 2006-12-12
Anyone else think this should be a bug submitted? I'd submit it myself if I didn't find the Ubuntu launchpad website so convoluted.

---

### Post by igknighted on 2006-12-12
You can create a home or trash applet on the panels and drag it onto the desktop I believe.

---

### Post by altonbr on 2006-12-13
But don't you see, that's not logical. That seems like a dirty Windows hack around some problem that shouldn't be there in the first place.

Would it not make more sense to you, to be able to right-click the desktop and CHOOSE what shortcuts you'd like on there. I'm not talking about adding programs to the desktop, because that can be done through the Applications list, but Home folders is a big thing.

I think XFCE is the most convoluted of all. It'd be nice to see all three work on a similar method of executing this "bug".

---

### Post by altonbr on 2007-09-16
(1 Year later)

Any news if they're gonna turn these on by default yet?

---

### Post by gottferdamnt on 2007-10-23
Desktop shortcuts are totally useless... XFCE works like e17, no optimization for these kinds of feature.

---

