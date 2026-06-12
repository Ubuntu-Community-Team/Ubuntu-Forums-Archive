---
title: "Adding directory launcher to desktop"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-10-07
Dumb question of the day... supposing I have an existing directory called 'foo'.  How to add it to the desktop so I can click an icon called 'foo' and be browsing that directory?  I am thinking I can create a directory called 'foo' in my desktop directory then link it to the real one, but there's gotta be an easier way.

---

### Post by jordanmthomas on 2006-10-07
make a launcher that launches this command
```
nautilus foo
```

---

### Post by crokett on 2006-10-07
geez.  that easy.  thx.  I was trying the windows equivalent of just putting the path I wanted in the command line but it kept telling me I wasn't allowed to run '/'. :)

---

### Post by jordanmthomas on 2006-10-07
No problem.
Just so you know, you could replace nautilus with whatever filemanager you want to use...konqueror, rox, even firefox

---

### Post by crokett on 2006-10-07
> **jordanmthomas said:**
> No problem.
Just so you know, you could replace nautilus with whatever filemanager you want to use...konqueror, rox, even firefox

thx for the tip. trying to make it as easy as possible for my wife to use her account. I do most of my work ssh'd in at the command line - haven't really ever learned any of the linux gui's.

---

### Post by jaboua on 2006-10-07
> **crokett said:**
> I was trying the windows equivalent of just putting the path I wanted in the command line but it kept telling me I wasn't allowed to run '/'. :)
Just so that you know: that is possible as well, but in the shortcut properties you have to change the type from "command" to "link to url", "link to folder" or something like that in the drop-down box.

---

### Post by CatKiller on 2006-10-07
As a point-and-click alternative for those that don't want to get their feet wet:

Browse to the folder you're interested in in Nautilus.

Go to Bookmarks, and Add Bookmark. The folder will now appear in the Places menu.

Open the Places menu and click-and-drag the Bookmark representing your folder to the Desktop. Release the mouse button.

You now have a launcher on the Desktop to that folder.

---

