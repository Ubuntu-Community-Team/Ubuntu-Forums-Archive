---
title: "[SOLVED] help, gnome splash"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-02-01
Hello

I cannot change gnome splashscreen, I tried gconf-edit and gnome-splash screen-editor
I get errors about permission denied, read only /apps/gnome-session/options/show_splash_screen when I try to enable it,I even tried it with:
         $sudo -s 
         # gconf-editor

gnome-splash screen-editor wont start for the same reason, readonly /apps/gnome-session/options/show_splash_screen

---

### Post by (((X))) on 2008-02-02
here is my screenshot:

---

### Post by angry_johnnie on 2008-02-02
Well, I haven't used that particular app, but have you tried   gnome-splashscreen-manager?  It's in the repositories, and it's very easy to use.

---

### Post by (((X))) on 2008-02-02
Thanks angry_johnnie, I already tried that one.
But after I run this application, It isn´t loading, there is more.
When I click on logout, turn off, restart buttons disappear.
So I uninstalled gnome-spashscreen-manager.

Now I know how to enable splashscreen via gconf-editor
I selected show_splash_screen,
File-> ´new standard/basic window´ made show_splash_screen writable:)

---

