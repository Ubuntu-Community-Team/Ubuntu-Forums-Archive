---
title: "How to create new menu on main panel"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by zeeple on 2008-04-15
Hi,  I am wondering if there is a way to create new additional menus on the main panel similar to 'Applications' 'Places' and 'System' in which I can place launchers of my own choosing.  Any tips?

---

### Post by ssadhale on 2008-04-15
Not sure if you can do that. However, you can always just drag and drop icons on the task bar. You can create a new launcher on the main taskbar. Right click on it - it will give you what you need.

---

### Post by zeeple on 2008-04-15
Right, I am aware of being able to add launchers and new drawers and all that to existing panels but I need (read: want) to create a new menu.

---

### Post by CJ56 on 2008-04-15
What about if you added a new Main Menu using the Add to Panel right-click & then took out all the stuff you didn't want to see in it using the Edit Menus right-click & added whatever apps etc you did want?

---

### Post by zeeple on 2008-04-15
That's a good idea, except that you cannot control the new main menu separately from the first main menu.  Removing/adding in one also affects the other. It needs to be it's own menu.

---

### Post by zvacet on 2008-04-15
You can add to panel drawer and put your lauchers in it.

---

### Post by zeeple on 2008-04-15
Thanks for tip, but a drawer is not the same as a menu.  Menu's and drawers have different behaviors:

* A menu can be labeled by name, and drawer only by an icon
* menu contents may have icon + name or only names, while drawers may only display icons
* A menu auto closes when something is selected form it, a drawer sometimes stays open
* Drawers have some weird auto-hide thing going on, menus do not.

How does one create a new menu?  Does anyone know?

---

### Post by zeeple on 2008-04-16
Another thought:  perhaps there are menu packages that can be installed alongside gnome's default menu package?  Any ideas on that one?

---

### Post by 7raTEYdCql on 2008-04-16
You can go to Preferences-Main Menu- Add Menu

Tjat would basically another menu under your main menu.

---

### Post by zeeple on 2008-04-16
Thanks for the tip but that is not what I am looking for. I need a menu that exists independently of, and on the same level as the Main Menu.  In other words, I'd like to be able to move it over nearer the clock on the top panel. Thanks.

---

### Post by ace007 on 2008-04-16
AHA!

I think I stumbled upon something that can do what you want.  I think "gnome-menu-file-browser-applet" may be a solution.  I dont have ubuntu with me now, so I can't testify to the Gnome File browser's usefulness, because I haven't used it.  I think you can create a folder, fill it with shortcuts and then use the gnome-menu-browser-applet to place a drop down menu in the gnome panel.

The name appearing in the panel would be the name of the folder you created, so you can control the name, and then the shortcuts you place in the folder should appear as a drop down menu with icons and text.  HMMMMM....

Haven't tried it, just a thought

EDIT: Or maybe try [menu-file-browser-applet]("http://www.getdeb.net/app/menu-file-browser-applet")

---

### Post by zeeple on 2008-04-16
This is close!!  There are a few oddities with the package though:

1. right clicking seems to perform the same function as left clicking so you cannot reposition the applet on the panel, or remove it (via this method)
2. I have a series of launchers in a folder that, when placed in this new menu applet, no longer work. Instead, the launcher opens in gedit.

I think this one might be a work in progress but I have sent an email to the maintainer to see if I am missing something.

---

### Post by zeeple on 2008-04-17
ace007 is the winner. Here is the best link:

[http://code.google.com/p/gnome-menu-file-browser-applet/](http://code.google.com/p/gnome-menu-file-browser-applet/)

This is exactly what I was looking for.

---

### Post by zeeple on 2008-04-17
How does one give a forum "Thanks"?  I'd like to give ace007 one for finding this applet.

---

### Post by ace007 on 2008-04-17
Click the star on the bottom right of the post!  

Glad I stumbled upon something useful!

---

