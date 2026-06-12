---
title: "how to hide desktop folders?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-10
Hi,

I'd like to hide my desktop folders i created a side panel and moved miniversions of them there so i;d like to hide the folders now. i have pics on the desktop i want to keep but i want to hide the folders how can i do that?

---

### Post by Skye on 2006-06-10
If you right click on the folders and rename them so that there is a period before the filename, they will become hidden. For example, the folder "Music" would be renamed ".Music"

Of course, this will hide the folders from view, so to get them back to being visible you will need to open up the file browser and navigate to the Desktop folder, ("Desktop" on the Places menu at the top of the screen) and open up the prefrences menu (Edit -> Preferences) and select the "Show Hidden and Backup Files" and rename the files without the period in the beginning.

I hope this helps!

---

### Post by zugu on 2006-06-10
In the UNIX/Linux world, a hidden file or folder is one that has the "." (dot) character as the first character in its name. Examples:

/home/name/.fonts/

is a hidden folder, and

/usr/share/.file

is a hidden file.

So you just have to rename a file or folder, inserting a dot as a first character. To view hidden files and folders in Nautilus (GNOME's default window manager), just use the CTRL+H key combination, or choose View >> Show Hidden Files. Use this in your home folder and you'll see how many hidden files and folders are there.

I never tried hiding something on the desktop. It might work or it may not, because the desktop is a special folder.

If this does not work: try moving the folders in some other directory under your home directory and hide them there. 

Remember to update all the references to the files in those folders or to the folders themselves.

---

### Post by maddbaron on 2006-06-10
dang...i moved all my folders to my /home and created a link to back out and made the links panels for the side panel. didnt know it was that simple. well the more you know.

---

