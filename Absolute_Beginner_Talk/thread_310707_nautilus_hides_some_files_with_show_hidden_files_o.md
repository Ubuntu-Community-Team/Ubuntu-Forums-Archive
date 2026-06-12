---
title: "nautilus hides some files with show hidden files on"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by clownbarf on 2006-12-01
Hi all,

I have nautilus configured to show all files, but I just found out that it is hiding some files still. For example, /usr/share/applications/totem.desktop exists, I can see it from the terminal, but nautilus does not show it. Is there something else I have to configure to really "show all files"?

This is a new install of edgy i386.

---

### Post by CatKiller on 2006-12-01
It **is** showing it, but by a different name. Haven't you noticed that none of those files in Nautilus have the .desktop extension?

.desktop files are displayed in Nautilus using the name specified by the "Name=" line in the file itself. totem.desktop will be displayed in Nautilus as "Movie Player".

Some more information if you're interested:
[http://freedesktop.org/wiki/Standards_2fdesktop_2dentry_2dspec](http://freedesktop.org/wiki/Standards_2fdesktop_2dentry_2dspec)

---

### Post by clownbarf on 2006-12-02
The thought did occur to me, but it was too bizarre to accept. Do all "file managers" in Linux behave this way? The natural expectation of a user is that the GUI accurately reflect the underlying file system without any need for "tribal knowledge" to understand what files actually are in the file system. Maybe I'm missing something, but this is way out in left field.

Thanks for your reply

---

### Post by CatKiller on 2006-12-02
> **clownbarf said:**
> Do all "file managers" in Linux behave this way? 

I have no idea - I've only used Nautilus. As far as I know, though, .desktop files are special - all the launchers in your menu and panel and the like are .desktop files - and they're the only ones that don't get displayed by their filename. I could be mistaken though.

---

