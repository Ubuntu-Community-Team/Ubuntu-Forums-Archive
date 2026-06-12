---
title: "Click, Drag and Select"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2007-12-26
In Ubuntu, clicking on the desktop with the left mouse button and moving the cursor over multiple icons would select them. In Xubuntu however, this does not happen. When managing lots of documents and media files, this feature is extremely helpful. Is there anyway that I can enable it in Xubuntu? Thanks very much everybody.

---

### Post by Hospadar on 2007-12-26
Xubuntu uses a different desktop manager (xfce instead of gnome) and likely they just do not have that feature. (although it's entirely possible it is lurking in some menu somewhere, it seems unlikely they'd program it and not turn it on by default.

As an alternative, you might try using:
Ctrl-A to select all items
Ctrl-Left Click to select additional items (or deselect single items)

Also too, it may well be quicker to use a command line for that kind of manipulation
rm (to delete files)
rm -r (to delete non-empty folders)
mv /source/file /target/file/or_location (move or rename files)
mv -r (same as above, but for non-empty folders
cp source target (copy files)
cp -r source target


Note too you can use patterns in the command to pick out certain names of filetypes eg:
cp *.mp3 /home/luke (copies all files in folder that end in ".mp3" to /home/luke)

---

### Post by Crumpets and Jam on 2007-12-26
Thanks. Since making that post I have discovered that it works fine in Xubuntu's file manager, just not the desktop.

---

