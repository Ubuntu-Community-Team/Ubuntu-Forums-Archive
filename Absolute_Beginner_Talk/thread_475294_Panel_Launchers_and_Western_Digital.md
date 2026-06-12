---
title: "Panel Launchers and Western Digital"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-06-15
1) It seems that I'm unable to add a panel launcher that opens a folder. It says in the user guide that this is possible, but only gives instructions for oppening individual files. is there a way to make a panel launcher open a folder?

2) I have a Western Digital external drive. It mounts up and reads fine, but when I go to make shortcuts (links) to the folders inside, it says that that this opperation cannot be prefformed. how do i correct this?

3) When the WD drive mounts, an icon is put on both the desktop and in the Places menu. I'd like to find away to remove the icon from the desktop, but keep the link in the Places menu. Is this possible?


thanks in advance,
NoobGuy

---

### Post by Lapino on 2007-06-15
1) Just use custom application launcher, select "file" as type. When you just file://path/to/folder, this works.
2) No idea at the moment
3) You can change this behaviour, but not per volume (or not that I know off). It's either all volumes, or none. You can do this as follows:
* Press Alt+F2 (this open the run dialog)
* Type "gconf-editor"
* In the tree, go to "apps>nautilus>desktop"
* In the right pane, remove the checkmark next to "volumes_visible"

---

### Post by dasunst3r on 2007-06-15
My answer for question 2: I take it that your WD external hard drive has a FAT32 or NTFS file system.  Those do not support symbolic links.  Therefore, you have those shortcut .lnk files.

---

