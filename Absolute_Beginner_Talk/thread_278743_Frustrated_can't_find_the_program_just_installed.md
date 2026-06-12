---
title: "Frustrated: can't find the program just installed"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by yuliang on 2006-10-16
I installed the package bittorrent and bittorrent-gui using the synaptic package manager in Xubuntu. But I can't find the program I  just installed anywhere.

---

### Post by CatKiller on 2006-10-16
You can probably just type **bittorent** or **bittorent-gui** in a terminal. If you select the properties page for the package you've installed in Synaptic it will tell which files you've installed. Files in /bin or /usr/bin are the commands you could type in the terminal.

Sometimes you need to log out and log back in for changes to the menus to take effect.

EDIT: The commands are **btdownloadgui.bittorrent** and **btcompletedirgui.bittorrent**, but just double-clicking on a .torrent file should do.

---

### Post by K.Mandla on 2006-10-16
If I remember right, bittorrent-gui comes up as an execution option if you click on a torrent in your browser.

Alternatively, you might be able to hunt it down by entering

```
whereis bittorrent-gui
```
in a terminal window. ;)

---

### Post by doobit on 2006-10-16
> **K.Mandla said:**
> If I remember right, bittorrent-gui comes up as an execution option if you click on a torrent in your browser.

Alternatively, you might be able to hunt it down by entering

```
whereis bittorrent-gui
```
in a terminal window. ;)

You are correct. bittorrent just sits there in the background until you actually download a torrent and click on it to run it.

---

