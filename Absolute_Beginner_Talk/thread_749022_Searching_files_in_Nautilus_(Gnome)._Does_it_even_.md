---
title: "Searching files in Nautilus (Gnome). Does it even work?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by softtower on 2008-04-08
How do you find files in Gnome/Nautilus? I press Ctrl+F (or press the toolbar button that says "Locate files by name or content"). When I do that, it replaces the location bar with the search box. Perfect - I go ahead and type something. Hit Enter - nothing - "Search results" and a white window. It doesn't even appear to do anything. Anything at all - returns immediately.

I tried everything, including giving it an exact file name of what I am searching for - no results. WTF? How can something this huge and important to be broken and nobody cares?

By the way, if I do Places/Search for Files - that dialog appears to search.

---

### Post by jw5801 on 2008-04-08
Open a terminal and use```
locate *thing-you-are-looking-for*
```

---

### Post by Cannaregio on 2008-04-08
> **softtower said:**
> How do you find files in Gnome/Nautilus? I press Ctrl+F (or press the toolbar button that says "Locate files by name or content"). When I do that, it replaces the location bar with the search box. Perfect - I go ahead and type something. Hit Enter - nothing - "Search results" and a white window. It doesn't even appear to do anything. Anything at all - returns immediately.

Indeed strange.
Try this (assuming you have some txt files):
search for 
```
*.txt
```
does it give you a list with name, size, pemissions etc?

---

### Post by vanadium on 2008-04-08
The original question was: "Searching files in Nautilus (Gnome). Does it even work?" Using "find"or "locate" form the command line is not an answer, especially not to "absolute beginners". Exactly the same concern was posted here:

[http://ubuntuforums.org/showthread.php?t=590686](http://ubuntuforums.org/showthread.php?t=590686)

---

### Post by sayakb on 2008-04-08
@OP
Try catfish:
```
sudo apt-get install catfish
``` It has a good GUI.. (Applications->Accessories->File search)

---

### Post by ramjet_1953 on 2008-04-08
I believe that the current version is tightly integrated with [COLOR="Blue"]tracker.[/COLOR]

If you navigate to [COLOR="Blue"]System>Preferences>Control Centre[/COLOR] and when the window opens, scroll down to [COLOR="Blue"]Other[/COLOR] and select I[COLOR="Blue"]ndexing Preferences[/COLOR], you can customise how your system indexes things.

Of course, if you have tracker turned off, Nautilus cannot find anything on a search.

Regards,
Roger :cool:

---

### Post by niteshifter on 2008-04-08
Hi,

Yes it works. But depending upon which version of Ubuntu/GNOME you have the way it works varies::

6.10 (Edgy) - Front end for the find command, searching within files for a simple pattern match (no wildcards).

7.04 (Feisty) - I dunno, I skipped this release.

7.10 (Gutsy) - As ramjet-1953 said, works with Tracker. Put another way: combines filename searching with file content searching.

8.04 Beta (Hardy) - It's beta software, maybe it works, maybe it doesn't. Maybe it works this time, but not the next. Maybe it works one time after a restart / reboot. Maybe it works subject to planetary alignment in conjunction with asteroid orbits and gravity waves from near galaxies ... that's what "beta" means ;)

---

### Post by ad_267 on 2008-04-08
I'm using Gutsy, doesn't work for me. The integrated searching in nautilus never finds anything. The only way I can search for files is going Places - Search for Files. If i try Applications - Accessories - Tracker Search Tool it doesn't work, even though under System - Preferences - Indexing Preferences, indexing is enabled.

Edit: Also this used to work but probably stopped working after an update. See here: [http://ubuntuforums.org/showthread.php?t=588143](http://ubuntuforums.org/showthread.php?t=588143)

---

