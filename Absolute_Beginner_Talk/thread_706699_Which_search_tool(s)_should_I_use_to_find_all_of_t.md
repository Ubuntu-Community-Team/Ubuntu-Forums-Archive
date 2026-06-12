---
title: "Which search tool(s) should I use to find all of the icons (xpm-files) in Ubuntu?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-24
**[COLOR="Green"]I can find icons via the desktop-panel in Ubuntu 7.04, but I need to know if any of you would please tell me how would you find all of the [B]other**.xpm-files that are *not* listed in the "Browse Icons" window/search tool?

There are only 3 search-tools that I've used to find icons:
1. Search for Files... (located in the Places panel-menu)
2. Tracker Search Tool (located in the Applications panel-menu)
3. File Browser (it appears when you click on a folder on your desktop, in Ubuntu)[/COLOR][/B]

[COLOR="Magenta"]**Thanks for taking your time to read this message. lease tell me what you think I should do to solve this problem.**[/COLOR]

---

### Post by Crooksey on 2008-02-24
```

$ sudo updatedb
$ locate *.xpm
```

---

### Post by ahuman on 2008-02-24
> Would any of you please give me step-by-step instructions about how to change those default icons to the correct icons, like the icons can be changed in the desktop-panel?

For example: This icon is not the correct icon for iTunes:

[img]http://img238.imageshack.us/img238/8918/itunesexewx5.png[/img]

---

### Post by Crooksey on 2008-02-25
```

$ sudo updatedb 
$ sudo locate *.xpm 
#here it will list a file locations of all .xpm files, copy the path to the itunes.xpm file..
$ sudo cp /path/to/itunes/file.xpm /home<username>/Desktop/

```

Thats as close as I can get without physically doing it, in the world of free help via other users, no-one is going todo everything for you.

---

