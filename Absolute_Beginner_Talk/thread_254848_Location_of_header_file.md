---
title: "Location of header file"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by greymaus on 2006-09-10
Can someone tell me where the header file 'ncurses.h' is to be found in Breezy Badger?  It should be in the /usr/include directory, but it's not. And according to my package manager, the header file is present, so it must be *somewhere!*

---

### Post by mlind on 2006-09-10
Headers are usually separated to -dev packages, so you need to install **libncurses5-dev** package.
```

sudo aptitude install libncurses5-dev

```

---

### Post by greymaus on 2006-09-10
Thanks for your quick reply...Yes, I already have the libncurses5 libraries installed. That's not the problem. The problem is that I can't find the directory where the header file (as in "include ncurses.h" in my c program) is located. Most usually, that file is in /usr/include; this time it's not. And without the header file, the libraries are useless, because as you no doubt know, the header file directs the gcc compiler to the site of the library.

---

### Post by greymaus on 2006-09-10
Ok, I stand corrected. I downloaded the wrong libncurses file--the one without the 'dev' at the end.](*,) So I went ahead and downloaded *all* the libncurses files I could find; and now I finally have an ncurses.h header file in /usr/include. 

Gad. Sometimes I wonder if it wouldn't be easier just to go back to scratches on clay tablets...

---

### Post by mlind on 2006-09-10
> **greymaus said:**
> Ok, I stand corrected. I downloaded the wrong libncurses file--the one without the 'dev' at the end.](*,) So I went ahead and downloaded *all* the libncurses files I could find; and now I finally have an ncurses.h header file in /usr/include. 

Gad. Sometimes I wonder if it wouldn't be easier just to go back to scratches on clay tablets...

You probably don't need all libncurses packages, just libncurses5-dev and its dependencies. But next time you run into same problem, remember that headers are almost always in -dev packages.

One very nice tool for finding a package for certain file is **apt-file**
```

sudo aptitude install apt-file
sudo apt-file update
apt-file search ncurses.h

```

---

