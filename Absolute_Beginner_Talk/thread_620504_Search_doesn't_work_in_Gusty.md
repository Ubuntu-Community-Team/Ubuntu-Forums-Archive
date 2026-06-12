---
title: "Search doesn't work in Gusty"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-11-22
I used search pretty often to find music files on my machine and for some reason gusty never shows any results.  Even if I match the name exactly with the file name, it never brings up any results ever.

So what's up with this one?

---

### Post by Ubun2User on 2007-11-22
Are you selecting the right folder to look in?

---

### Post by MegaJim on 2007-11-22
What tool are you using to search ?

Have you tried updating the slocate database?

```
sudo updatedb
```

---

### Post by Billy_McBong on 2007-11-22
what are you using to search?
i think tracker(installed by default) works pretty well

---

### Post by CryptiniteDemon on 2007-11-22
I'm using the one that comes default with gusty.

when you're in a folder and hit Ctrl-F and then type in the search field at the top of the window.

It worked fine in Feisty, but not a damn thing in gusty.  And yes I am selecting the correct folder for whoever asked.

---

### Post by philinux on 2007-11-22
I would report this as a bug it dont work for me either

---

### Post by foxmulder881 on 2007-11-22
Do you have your data on a separate partition from the linux file system?
If so, you must configure Tracker to index your other partitions.

Go to: **System>Preferences>Indexing Preferences** and then click on the **Files** tab. Now locate the directory of the mount you want Tracker to index for search.

---

### Post by davidvolvox on 2007-11-22
Tracker worked for me at first on Evolution and files but not any more. As others report it returns a nul search. I have tried setting file preferences but it makes no difference.

---

### Post by CryptiniteDemon on 2007-11-22
Yeah, but the default option is for it to index all mounted drives.  So it makes no sense that it wouldn't index my drives properly.

I added it anyway, and still no results.  Do I need to restart?

---

### Post by mjpatey on 2007-11-22
I have the same problem on Gutsy.  Neither Tracker nor the original Search function return anything at all.

I'd be interested to know how to resolve this one!

---

### Post by foxmulder881 on 2007-11-22
A message to all with this problem, it sounds as though you haven't let your PC idle enough for search to index your directories.

Walk away from your PC and leave it for a couple of hours. Upon idle, Tracker will begin indexing your data and ready for searching.

I use Tracker on a daily basis because I'm so disorganized with my data on my partitions and I have no problems whatsoever.

---

### Post by mjpatey on 2007-11-22
Hi,

My computer idles all night, and most of the day when I'm not using it (stays on 24/7).  In my case, this is not the problem!

---

