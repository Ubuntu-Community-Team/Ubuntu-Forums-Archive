---
title: "Making a New Folder"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2006-12-01
I have edgy installed an would like to make a new folder on the company server...It will not let me, no error message, just sits there like I have not given a command.  I go to places, network servers, down the path to where I need to be, it asks me for password then lets me in, I can copy, view, write, change files but I cannot do anything with the folders.

---

### Post by LLRNR on 2006-12-01
Go ("**cd**") to the folder which will be the "parent" of the new folder you want to create and then
```
mkdir NameOfNewFolder
```
If you get an error message about permissions, it means you have to be "sudo" to be allowed to make / remove / rename / delete / copy / move things in that area... so use "sudo" in front of any such command.

(Sorry I have almost no GUI knowledge, I find it a lot easier to work with the CLI instead)

I just remembered: if you want to open the file manager in sudo mode, then hit Alt+F2 and enter:
- for Gnome: "*gksudo nautilus*" or
- for KDE: "*kdesu konqueror*".

HTH,

LLRNR

---

### Post by Hillbilly Tilley on 2006-12-01
Let me restate....I can open and copy files.  I cannot cut, move, rename, or overwrite files.  I cannot do anything with the folders.  This is a smb:// , which I cannot get to with the cd command.  Sometimes I get this is a directory error.

Any thoughts?

---

### Post by echo $USER on 2006-12-01
> **Hillbilly Tilley said:**
> Let me restate....I can open and copy files.  I cannot cut, move, rename, or overwrite files.  I cannot do anything with the folders.  This is a smb:// , which I cannot get to with the cd command.  Sometimes I get this is a directory error.

Any thoughts?

You can cd to it if you mount it.  It's a read-only file system which explains open and copy but no rename, overwrite.

---

