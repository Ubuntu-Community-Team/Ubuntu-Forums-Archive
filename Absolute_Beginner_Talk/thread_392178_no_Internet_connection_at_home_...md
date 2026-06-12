---
title: "no Internet connection at home .."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by emacsuser on 2007-03-24
I have no Internet connection at home. I can download and burn CDs from the office. I understand a lot of the extra stuff is available online. Can I download these packages to a CD and install the extras without going online.

---

### Post by chili555 on 2007-03-24
You can. Please go here, [http://packages.ubuntu.com/](http://packages.ubuntu.com/) You can search for the packages you want, download the .deb file and burn a CD. Take care about the dependencies of the package you wish to install; those are mentioned with a red dot. If you are not sure they are installed on your system, download those, too.

Simply install them with:```
sudo dpkg -i <package_downloaded>.deb
```Good luck!

---

### Post by jeffathehutt on 2007-03-24
You can download any packages you need from [http://packages.ubuntu.com]("http://packages.ubuntu.com")

If you do that, however, you will have to manually resolve any dependency problems that might show up.  In other words, you may have to download 5 packages just to install the one package you want.

---

### Post by buuntuu! on 2007-03-24
if you don't want to download all the single packages, there is [www.cargol.net](www.cargol.net)
the edgy-repositories (main, universe, multiverse) can be downloaded there (~14gig)
but their site seems to be down right now...
EDIT: you can find the torrents at isohunt :)

---

### Post by emacsuser on 2007-03-24
Thanks for the quick response. Will give it a try ..

---

