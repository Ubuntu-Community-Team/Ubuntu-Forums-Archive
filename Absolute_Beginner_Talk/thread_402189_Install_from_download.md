---
title: "Install from download"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-04-05
ok, i dont know how to install programs using downloaded files, example of this is i have an older laptop with only a dial up internet connection, and i dont have a pcmia card yet, how can i download a program, like from sourceforge, and install it, i have never learned, it has all been app-get install, could somebody help me.....

---

### Post by zvacet on 2007-04-05
If you download from sites try to download deb file(if is available).Put it in some folder(for example xfolder).After that
```
cd /xfolder
```
and where you are in xfolder
```
sudo dpkg -i file_name
```
or you can just right click on file and you will see gdebinstaller.Just click.

---

