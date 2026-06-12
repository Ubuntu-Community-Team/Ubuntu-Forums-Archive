---
title: "Shortcut or Link to XP folder??"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-06-09
I have a shared music folder on my xp machine. I can access it from dapper no problem. But I would like to have a desktop shortcut or first level menu link to that folder, so I dont have to navigate through 5 menu levels to get there. I have tried right clickin the folder and choosing create link but I get an error

```
Error "Unsupported operation" while creating a link to "smb://hal2...y%20Music".
```

is there another way to do this? Also is there anyway to show the current network address in an address bar like in windows explorer? :-s

---

### Post by Jagot on 2006-06-09
When in Nautilus when you're in the correct folder you could go to Bookmarks, Add Bookmark.  Then it will show up in your places menu.

---

### Post by dvarsam on 2006-06-09
Dear "rubrboots",

To create a Shortcut to an NTFS partition, do the following:

1. Mount the NTFS Partition either manually or through your "fstab" file (automated way).
(My entry on my "fstab" file looks like this: ```
/dev/sdb1       /mnt/ntfs_files  ntfs   nls=utf8,umask=0222  0  0
```

2. Right-click somewhere on your Desktop.

3. Select "Create Launcher..."

4. Under "Name:", type any name you would like.

5. Under "Command:", type the path to the NTFS directory you want to connect to - e.g. ```
nautilus "/mnt/ntfs_files/For Evaluation"
```

Your shortcut should now be created!

You could then go & check it out!

Good Luck!

---

