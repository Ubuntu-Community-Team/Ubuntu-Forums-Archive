---
title: "Gnome: Make sweet menus?"
date: 2009-06-13
forum: Art &amp; Design
---

### Post by nwarrenfl on 2009-06-13
Hi everybody!

I've been using Gnome since years, but yesterday i tried KDE and i must admit this desktop is very good, i especially liked the fact that Plasma looks very nice and that KDE is with one panel by default.

However i still use Gnome, and i personally don't like the menus, so i looked around on the web and found some projects like Gnome main menu and GnoMenu, but no one is as good as KDE's Raptor.

**_So i tought, wouldn't it be nice if there was a Gnome applet that would show a menu defined in a GtkBuilder file?_** This would mean you would be able to design menus by using the Glade interface designer and use them as themes for the menu applet.

I will maybe give this idea a try and make an applet. I will the names of each widget so that it would be the same for every theme.

For example: menu_search_entry as identifier for the search function for all themes, so coding the core of the applet would be simple and it would be just a matter of designing interfaces and using the defined names.

What is your opinion? Is it a good idea?
All comments or suggestions are welcome...

---

### Post by rylleman on 2009-06-13
I think it's a great idea!
Basically all Gnome-themes are the same, a little different icons, a little different frames etc. but generally it's the same setup.
Having a powerful tool like this to change the menus from a deeper level would open up for a lot of interesting solutions and looks.

---

### Post by MasterNetra on 2009-06-13
> **rylleman said:**
> I think it's a great idea!
Basically all Gnome-themes are the same, a little different icons, a little different frames etc. but generally it's the same setup.
Having a powerful tool like this to change the menus from a deeper level would open up for a lot of interesting solutions and looks.

+1

Its about time for gnome to upgrade its appearance capabilities if it is to compete with KDE. ^.^

---

### Post by nwarrenfl on 2009-06-14
Thanks for answering.

I've created a little prototype and i'll show it once i have something that really works.

The problem is that i don't know if we could make themes that do not look like GTK+, my idea was to make a GTK+ looking menu, but why not make it themeable, anybody knows if it is possible?

I am also searching an original name if i would ever be able to finish it! :D

---

### Post by Giant Speck on 2009-06-14
If anything, I'd like the ability to create a simple custom menu on the panel.

---

### Post by nwarrenfl on 2009-06-14
You mean custom menus by editing your own theme or by using an user interface?

---

### Post by Giant Speck on 2009-06-14
> **nwarrenfl said:**
> You mean custom menus by editing your own theme or by using an user interface?
 
I mean a panel applet that allows me to make a custom menu.
 
For example, by default, you have the Applications, Places, and System menus.  It'd be nice to create my own menu, too.

---

### Post by days_of_ruin on 2009-06-14
> **nwarrenfl said:**
> Thanks for answering.

I've created a little prototype and i'll show it once i have something that really works.

The problem is that i don't know if we could make themes that do not look like GTK+, my idea was to make a GTK+ looking menu, but why not make it themeable, anybody knows if it is possible?

I am also searching an original name if i would ever be able to finish it! :D

How far is the prototype? Can I see the source?
Do you want/need any help?

---

### Post by nwarrenfl on 2009-06-14
> **Giant Speck said:**
> I mean a panel applet that allows me to make a custom menu.
 
For example, by default, you have the Applications, Places, and System menus.  It'd be nice to create my own menu, too.

Well you would certainly be able to do that by simply editing the user interface file, maybe custom menus could be added (nice feature), but i'm far away from such an applet.

---

### Post by nwarrenfl on 2009-06-14
> **days_of_ruin said:**
> How far is the prototype? Can I see the source?
Do you want/need any help?

I've been able to make something interesting, you can watch a preview of the prototype [here]("http://nwarrenfl.open-web.fr/ganjup/Menew.avi")...

Any comments and/or suggestions are welcome.

The next step will be to add the categories...

---

### Post by days_of_ruin on 2009-06-14
> **nwarrenfl said:**
> I've been able to make something interesting, you can watch a preview of the prototype [here]("http://nwarrenfl.open-web.fr/ganjup/Menew.avi")...

Any comments and/or suggestions are welcome.

The next step will be to add the categories...

What language is it written in?

---

### Post by nwarrenfl on 2009-06-14
It's written in C using GLib, which makes it very easy (by using GAppInfo)
The themes are GtkBuilder files...

I still search a good name! ;)

---

### Post by dudu-sama on 2009-08-10
hi nwarrenfl !

I am really very interested by your idea !
Is it possible to try it ?

very good work !!

ps : tu peux me contacter en francais par mp si tu veux ^^

thx

---

