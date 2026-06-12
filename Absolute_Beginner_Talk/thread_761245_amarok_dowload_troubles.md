---
title: "amarok dowload troubles"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by musicguy on 2008-04-21
hey, im pretty new with Ubuntu. i've been having some troubles with rhythmbox so i decided to go to the add/remove apps. and get Amarok but everytime i try it gives me this and im not sure what it means..

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any help would be much appreciated, thanks!

---

### Post by billgoldberg on 2008-04-21
> **musicguy said:**
> hey, im pretty new with Ubuntu. i've been having some troubles with rhythmbox so i decided to go to the add/remove apps. and get Amarok but everytime i try it gives me this and im not sure what it means..

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any help would be much appreciated, thanks!

Read the error message. 

Unlike windows error messages, the ubuntu errors actually help.

Like it says, dpkg was interupted, so now you must open a terminal and type (copy/paste)

```
sudo dpkg --configure -a
```

(I don't know if sudo is needed).

(You can open a terminal by going to applications -> accessories -> terminal)

BTW: If you want to download and run amarok without any problems (no mp3 support, ...) you'll need to download it from the medibuntu repo.

Take a look here for that.

[http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/](http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/)

---

### Post by musicguy on 2008-04-21
hey thanks it worked!

---

