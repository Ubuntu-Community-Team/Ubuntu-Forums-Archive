---
title: "Moving desktop icons to sidebar"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-11-03
Hi, how do I get desktop icons[drive/partitions] to go to my sidebar, tried drag&drop and other things but no go.](*,) 
TIAFAI

---

### Post by jpeddicord on 2006-11-03
I don't think it is possible as of now to add network or partition drive icons to the panel. Right click on a blank spot on the panel and click Add to Panel, you may find something suitable there.

Jacob

---

### Post by CatKiller on 2006-11-03
You can add normal launchers to the panel, though. If you drag-n-drop the entries from the Places menu, you'll get a launcher on the panel.

If you don't have your mount points in the Places menu, you can add them easily enough by adding a bookmark in Nautilus. Personally, I put launchers like these in a drawer on the panel.

If you don't want the icons on the desktop any more, you can open **gconf-editor**, navigate to /apps/nautilus/desktop, and untick volumes_visible. Or mount those partitions to somewhere other than /media.

---

### Post by randiroo76073 on 2006-11-04
Thanks all, CatKiller the drawer thing is the ticket I was looking for, just couldn't seem to get there, bookmarks did trick :)

---

