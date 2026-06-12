---
title: "[SOLVED] Firefox-Missing Files"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-10-13
I have a couple of corrupt extensions which I uninstalled and reinstalled with no joy.

Went to Home/Files/Etc/ Firefox/Profile looking for Extension,ini, Extsion.cache and Extension.rdf in order to delete them. They would be replaced on next FF boot.

Well, these files were not to be found. Only things in the Profile folder are Localstore, Mime types and Search .rdf and Bookmarks.html.

Did I look in the right place, and if so, why didn't these Ext. files show up?

Thanks for any help,

Jon

---

### Post by milosz.galazka on 2007-10-13
go to directory *~/.mozilla/firefox/* and you will see folder with your profile...

---

### Post by Romin-1 on 2007-10-13
Thanks milosz,

This is weird, still cannot find the Extension.ini,RDF,and cache files.

Tried deleting the Localstore and that didn't help.

The extensions were working and somehow got corrupted.

Oh well,

---

### Post by milosz.galazka on 2007-10-13
You see something similar?
```
milosz@bluebird:~$ ls ~/.mozilla/firefox/aj5w6511.default/
adblockplus        cookies.txt       install.log     session.rdf
blocklist.xml      downloads.rdf     key3.db         sessionstore.js
bookmarkbackups    dta_history.xml   localstore.rdf  signons2.txt
bookmarks.bak      extensions        lock            urlclassifier2.sqlite
bookmarks.html     extensions.cache  mimeTypes.rdf   XPC.mfasl
Cache              extensions.ini    prefs.js        xpti.dat
cert8.db           extensions.rdf    SDThumbs        XUL.mfasl
chrome             formhistory.dat   search.rdf
compatibility.ini  history.dat       search.sqlite
compreg.dat        hostperm.1        secmod.db

```
*aj5w6511.default* is my profile

What about safe mode?
```
 firefox --safe-mode
```

---

### Post by Romin-1 on 2007-10-13
Finally found them and all is joyful now.

Thanks Milosz

Jon

---

