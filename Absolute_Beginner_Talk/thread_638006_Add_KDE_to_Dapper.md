---
title: "Add KDE to Dapper"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by hobo on 2007-12-11
When trying to add kbuntu-desktop on my Dapper installation I get the following:

WARNING: The following packages cannot be authenticated!
  libpoppler1-qt
Install these packages without verification [y/N]? y
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main libpoppler1-qt 0.5.3-0ubuntu1
  The HTTP server sent an invalid reply header
Failed to fetch [http://www.beerorkid.com/compiz/pool/main/p/poppler/libpoppler1-qt_0.5.3-0ubuntu1_i386.deb](http://www.beerorkid.com/compiz/pool/main/p/poppler/libpoppler1-qt_0.5.3-0ubuntu1_i386.deb)  The HTTP server sent an invalid reply header
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Nothing will DL. What do I do? This method worked just fine on Gutsy laptop.

Kirk

---

### Post by Kingsley on 2007-12-11
Try this.
```
sudo apt-get update --fix-missing
```

---

### Post by hobo on 2007-12-11
Same error after using the --fix missing

---

### Post by hobo on 2007-12-11
I got around this problem by just installing kdebase....That is all I need for this platform. tks

---

### Post by rsambuca on 2007-12-11
What is that beerorkid repo?  Why not just remove it from your sources?

---

