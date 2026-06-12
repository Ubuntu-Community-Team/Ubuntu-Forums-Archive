---
title: "Ho to modify Documents path into Gnome Resources menu"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Netcab on 2007-12-04
I've a dual boot system, configured as follow:
Drive 1: sda
sda1	windows XP boot partition
sda5	Linux swap
sda6	Linux root
sda7 	Linux /home

Drive 2: sdb
sdb1	NTFS data drive

I've seen that Ubuntu has the menu Resources that has links to Documents, Images, Music and Videos into the home directory of sda7.
I would like to link these directories to the similar directories I have on the sdb1 partition, instead. 
I konw that I could create a symbolic link, but I'd prefer to point to the destination directory on sdb1 as soon as I click the "documents" item into the Gnome Resources menu.
Is it possible ?

---

### Post by Miguel on 2007-12-05
> **Netcab said:**
> I've seen that Ubuntu has the menu Resources that has links to Documents, Images, Music and Videos into the home directory of sda7.
I would like to link these directories to the similar directories I have on the sdb1 partition, instead. 
I konw that I could create a symbolic link, but I'd prefer to point to the destination directory on sdb1 as soon as I click the "documents" item into the Gnome Resources menu.
Is it possible ?

I suppose you are talking about the menu item between "Applications" and "System", aren't you?. In that case, you can change that somewhat easily. These directories are defined in a file, so we will be editing that file to make it point to your desired dirs.

Open a terminal and type (if gedit is not your editor of choice, change accordingly):
```

gedit ~/.config/user-dirs.dirs

```

No sudo is needed here. You will see a small file with some "sharps" which comment out the rest of the line and some lines with self-explanatory stuff such as XDG_VIDEOS_DIR. Edit this file to your content, although it'd be wise if you pointed to places where you have full permissions. For example, my .config/user-dirs.dirs looks like this:
```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/descargas"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Desktop/Documentos"
XDG_MUSIC_DIR="$HOME/musica"
XDG_PICTURES_DIR="$HOME/imagenes"
XDG_VIDEOS_DIR="$HOME/Videos"

```

As an added bonus, you might be interested to know that, for example, some music programs will have XDG_MUSIC_DIR in its quick bookmarks (in open/save dialogs) and firefox will do the same with XDG_DOWNLOAD_DIR. You get the idea.

Save your document and close gedit. However, we're not done. For these changes you still have to run (again from a terminal)
```

xdg-user-dirs-gtk-update
xdg-user-dirs-update

```

We're done! Well, you might need to restart gnome: just close the session and log in again. But, we're done.

Hope this helps,

Miguel

---

### Post by DragonKore on 2007-12-05
Ooh, that's handy to know. I just made shortcuts to the folders on my second hard drive and put them in Nautilus' sidebar. This is even better though.

---

### Post by DragonKore on 2007-12-05
So, uh, I deleted those original directories in Home for "Documents," "Pictures," etc, and now I want them back so I can perform the above edit. Anyway to get them and have them show up in Places again?

---

### Post by Miguel on 2007-12-06
You can create these directories using either the terminal (the command is mkdir) or the file manager of your choice (Nautilus, Dolphin, Konqueror, Thunar...). However, there's no need to have the original ones. It only matters where the configuration file points to.

---

### Post by DragonKore on 2007-12-06
Doh, I forgot to run the code at the end, that's why I was confused. Thanks, mate.

---

### Post by Netcab on 2007-12-08
I tried what you suggested but it didn't change.
this is the original 

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Scrivania"
XDG_DOWNLOAD_DIR="$HOME/Scrivania"
XDG_TEMPLATES_DIR="$HOME/Modelli"
XDG_PUBLICSHARE_DIR="$HOME/Pubblici"
XDG_DOCUMENTS_DIR="$HOME/Documenti"
XDG_MUSIC_DIR="$HOME/Musica"
XDG_PICTURES_DIR="$HOME/Immagini"
XDG_VIDEOS_DIR="$HOME/Video"

I have modified it in this way:
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Scrivania"
XDG_DOWNLOAD_DIR="$HOME/Scrivania"
XDG_TEMPLATES_DIR="$HOME/Modelli"
XDG_PUBLICSHARE_DIR="$HOME/Pubblici"
XDG_DOCUMENTS_DIR="/media/sdb1/Archivio"
XDG_MUSIC_DIR="/media/sdb1/Archivio/Musica/Musica"
XDG_PICTURES_DIR="/media/sdb1/Archivio/Immagini"
XDG_VIDEOS_DIR="/media/sdb1/Archivio/Video"

I run the commands:
xdg-user-dirs-gtk-update
xdg-user-dirs-update
also as sudo and tried also to reboot the machine, but nothing: it still point to the originals dir.

---

### Post by Miguel on 2007-12-09
Mmm... it may be that only directories under $HOME are considered valid. Because I suppose you do have read/write permissions in sdb1 (thanks to ntfs3g). Anyway... I'll have to do a couple of tests to see which reason is the one hampering you.

---

