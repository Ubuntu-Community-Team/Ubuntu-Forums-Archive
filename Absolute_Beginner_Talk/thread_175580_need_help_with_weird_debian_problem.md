---
title: "need help with weird debian problem"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-05-13
i'm working on my neighbor's computer. some of his students installed debian on it. i'm trying to put some education type programs on it for his kids, but the menus won't update. i've already tried 'fix desktop menu' and *su update-menus*. is there anything else i can try? like updating the db, maybe? it's gnome, btw.

---

### Post by mority on 2006-05-13
Why not just add the menu entry by hand?

---

### Post by fuscia on 2006-05-13
[QUOTE=mority]Why not just add the menu entry by hand?[/QUOTE]

even simpler is to drag an icon onto the desktop from nautilus. does the gnome menu not have a way to be updated? (i don't use gnome.)

---

### Post by skymt on 2006-05-13
Many packages don't come with menu entries. Ubuntu has Alacarte so you can add your own, but I don't know how well it would work in Debian (assuming you're using Debian stable). The easiest fix would be to add launchers to the panel (right click a panel > Add to panel... > Custom Application Launcher). If you need more organization, you can add drawer panel applets.

---

