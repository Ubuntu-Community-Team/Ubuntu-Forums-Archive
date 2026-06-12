---
title: "searching with nautilus"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2008-03-15
Can someone please tell me how the search function is supposed to work...

Even when I know exactly the file name and set the filter to where the file is located....nothing comes up

I mean...like when i use windows...i go to start>search> and everything pretty much gets found...

What do I do with Ubuntu?!?!?

---

### Post by vexorian on 2008-03-15
Are you using nautilus' find file option? Try with places\find archives, or if you are on gutsy with deskbar.

---

### Post by ICUR2Ys on 2008-03-15
Have you considered entering in terminal window:  locate filename

If nothing comes up it means file not found.

---

### Post by Hmarroqu on 2008-03-15
well the situation is...I have a CD with a ton of apps for my centro...and need to be able to be in nautilus and say...hmm..i want to find all the "clock" apps....so i tried typing that into the search option in the nautilus window....figuring it would kinda show me all those files with that in the name..i even used the filter option...
I was just in shock how when I type the full name of a file and its type...(as a test) no results come up...its weird...i dont get it

---

### Post by vexorian on 2008-03-15
I just don't get results in Nautilus search, I am not sure how it is supposed to work, it is time vexorian submits a bug report...

Just use the places \ search files... option in the top menu. It allows you to open the folder holding the found files in nautilus.

---

### Post by ramjet_1953 on 2008-03-15
Quite often this problem arises because of permissions.

Try opening Nautilus in Super User mode and try that.

Type this in a terminal:

[COLOR="Red"]gksu nautilus[/COLOR]

You will then be prompted for your password.

Regards,
Roger :cool:

---

### Post by ryanhaigh on 2008-03-16
The version of Nautilus provided in Ubuntu 7.10 (Gutsy) uses tracker to search for files. This means that only files which are indexed will be shown in the results. You can get around this by using the Find Files option in Places, installing [nautilus-search-tool]("apt://nautilus-search-tool") or if you are like me and don't use tracker you can follow my [howto on compiling nautilus without tracker]("http://ubuntuforums.org/showthread.php?p=4524368"), its easier than it sounds.

---

### Post by vexorian on 2008-03-16
Man, Canonical should really drop tracker, it is crazy how it is ruining everything. Nautilus should be able to search on non-indexed places, indexing should only improve performance, not be mandatory... oh gosh, so if I placed my USB disk I wouldn't be able to search... great.

---

### Post by ryanhaigh on 2008-03-16
Tracker is actually being disabled by default for Hardy, it will be available for those who want it but I am unsure as to whether you will be able to search with it in Nautilus.
[http://ubuntuforums.org/showthread.php?t=723216](http://ubuntuforums.org/showthread.php?t=723216)

---

