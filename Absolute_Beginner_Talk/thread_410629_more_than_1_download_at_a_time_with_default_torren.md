---
title: "more than 1 download at a time with default torrent program"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by noteforself on 2007-04-16
hi everyone,

i am using the default bittorrent program that comes with ubuntu.  i am downloading a file, and when i click on another .torrent file to try to download it, i get this error:

"couldn't listen

(98, 'Address already in use')"

Can someone help me?  Thanks in advance.

---

### Post by RomeReactor on 2007-04-16
Hi. The problem is Gnome-Bittorrent is assigned only **6881** as the download port; so open a terminal (Applications-->Accessories-->Terminal) and enter:

```
gconf-editor
```

There go to "Apps-->gnome-btdownload-->settings" and change the **max_port** to **6889**. Close Gconf and the terminal, and see if you can open multiple bittorrents now. Another way to do this (without changing ports in Gconf) is to open a terminal and enter:

```
 btlaunchmanycurses /home/USER_NAME/FOLDER_WITH_TORRENT_FILES
```

which is a terminal version of Bittorrent and will open **all** the .torrent files you have on FOLDER_WITH_TORRENT_FILES and save them to your home folder.

---

### Post by noteforself on 2007-04-16
thanks, you are awesome.

i did not know about this gconf-editor

---

