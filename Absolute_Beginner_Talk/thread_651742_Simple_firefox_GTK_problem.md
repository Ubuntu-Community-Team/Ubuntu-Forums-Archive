---
title: "Simple firefox GTK problem"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-12-27
Hey everybody,

I installed a new GTK2 theme.  It's a black theme with gray interiors.  It looks good with most things (except things which seem to require root access, such as add/remove and synaptic package manager, but I'm not concerned about that), but for some reason it's not working correctly in Firefox.  All of my drop down menus, such as the address bar or the google search show up black with black text.  I've read this is a problem with Firefox and not GTK.  Anyway, does anybody know a quick way I can get firefox to display text in drop down menus as white?

Thanks,

Helixed

---

### Post by spiderbatdad on 2007-12-27
in browser window...Edit>>Preferences>>Content>>Fonts and Colors...colors

---

### Post by helixed on 2007-12-27
This only changed the page content, and not the color of the menus.  Thanks for the quick reply, but any other suggestions?

Helixed

---

### Post by spiderbatdad on 2007-12-27
I'm almost sure it can be set from the about:config page in firefox's address window, but for the life of me I haven't found it yet.

---

### Post by spiderbatdad on 2007-12-28
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/117132](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/117132)

---

### Post by helixed on 2007-12-28
Okay, after doing some digging, I found out this problem could be fixed by altering the userChrome.css file located in the Mozilla folder in my home directory.  I simply pasted the code on this page into a text file and named it userChrome.css, and it fixed the problem completely.  Thanks for all the help.

Helixed

---

