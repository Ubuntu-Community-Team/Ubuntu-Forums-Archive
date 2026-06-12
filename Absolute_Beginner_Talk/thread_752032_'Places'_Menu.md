---
title: "'Places' Menu"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by kneewax on 2008-04-11
I was triyng to edit the paths for the folder location in the 'Places' Menu (and the open close dialogues).  I want to make the default folders (documents, music, video etc) open folders of the same name on my data partition which is formatted to FAT32)

  I editted the  ~/.config/user-dirs.dir

to look like this, as I read that would do what I wanted after a reboot:

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_MUSIC_DIR="/media/sda2/Music"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="/media/sda2/Documents"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PICTURES_DIR="/media/sda2/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos" 


However, despite the reboot the icons in the Places Menu still take me to the original folder locations in my home folder.

Any ideas what I am doing wrong?

---

### Post by munkyeetr on 2008-04-11
Open **nautilus** and then do the following:

**Bookmarks** -> **Edit Bookmarks**

Make your changes in this dialog.

---

### Post by kneewax on 2008-04-12
Brilliant - Thanks - that was much simpler!

Does anyone know if there is a way of getting custom icons in the Places Menu

---

