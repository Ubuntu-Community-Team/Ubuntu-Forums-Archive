---
title: "Gnome-Do Keybinding"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by PoetOfShadows on 2008-03-25
How do I reset the key-binding for Gnome-Do?

I accidentally messed it up, and can't get it back right.

Thanks in advance

---

### Post by Jadd on 2008-03-26
Here's how you do it:
[LIST][*]Press alt-f2
[*]Type: gconf-editor
[*]Press enter. A window with the title, Configuration Editor, should appear. Gconf is a system a lot of GNOME apps use to store their settings, including gnome do.
[*]On the left pane, browse to /apps/gnome-do/preferences
[*]In the left pane, you should see an entry called key_binding. Right-click on it, click edit.
[*]Change it to <Super>space
[*]The change should have been applied immediately. That's the beauty of gconf.
[/LIST]
There might be a simpler why to do it (there's definately a way to do it in one command in the terminal), but I don't know it.

---

