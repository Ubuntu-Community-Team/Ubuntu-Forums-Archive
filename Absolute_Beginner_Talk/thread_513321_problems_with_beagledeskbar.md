---
title: "problems with beagle/deskbar"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by linusl on 2007-07-30
i recently installed beagle so i would get beagle search results directly from deskbar when typing, but it's not working. i get a beagle entry in the settings for deskbar that i check, but the only thing that shows up when searching in deskbar is an entry that says "search for [word] with beagle", and i have to click that which brings up the normal beagle search window. i have restarted the computer and beagle seems to be done with all indexing. i get results when searching from the beagle window, but i get no results directly in deskbar.

on a related note, i get some fileresults, sometimes, no matter if beagle search is added to deskbar or not. this seems to be the deskbars default filesearch, but it's behaving really weird. i have a file on my desktop that begins with "[S^M] Na...", and it shows up in results when i type "[s^m] n", but not when i type the correct capitalization ("[S^M] N"), so it seems to be case sensitive, but in a really stupid way. i hope that if i get beagle search working that this won't be an issue though.

---

### Post by Pragmatist on 2007-07-31
[https://help.ubuntu.com/community/Beagle](https://help.ubuntu.com/community/Beagle)

---

### Post by linusl on 2007-08-01
thank you, that page told me exactly what i needed to know. i searched the forums but never thought to look at those help pages.

i was missing the python-beagle package, after installing that i restarted deskbar and i had a "beagle live" entry in the list of deskbar searches (the begle entry worked like it should from the start, just adding a way to start the beagle search window).
the beagle live search works as it should now. thanks again ^^

---

