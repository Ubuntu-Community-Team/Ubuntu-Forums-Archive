---
title: "Which is the best site to dload .deb install packages"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-02-21
Since I dunno how to install when i got .tar.gz2 or whatever source, I try to use .deb packages the most, and like this, I can transfer these and install apps on a computer which hasn't an internet connection via my USB Stick

---

### Post by 3rdalbum on 2008-02-21
[www.getdeb.net](www.getdeb.net) has good packages.

But I'd suggest you buy the latest issue of Linux Format magazine, the one with "Distro Heaven" on the cover. They have an ingenius solution to getting packages (and all the dependencies) for one Ubuntu computer, from another computer with an internet connection.

---

### Post by jachymc on 2008-02-21
[http://packages.ubuntu.com](http://packages.ubuntu.com)

but you can use also use 

apt-get install -d -o dir::cache=/media/flasdisk  "package_name" 

, which will download, but not install all dependency packages as well, then you can copy it to your flash disk and later install with dpkg -i *.deb

---

### Post by FrozenFox on 2008-02-21
[http://linuxappfinder.com/](http://linuxappfinder.com/)  is also a decent site, though not always up to date.

---

### Post by jachymc on 2008-02-21
you have to create also two directories on your flash disk

mkdir -p /media/flasdisk/archives/partial

---

### Post by seventhc on 2008-02-21
most tar.gz2 can be installed easily after unpacking them,
When I download one, instead of saving it to disk I choose the '*open with*' option and it's set to '*archive manager*'. When that opens I click on the extract button and put it on my desktop. Open a terminal and type in
note:Not all packages are installed thit way though, but they should have a readme file that tells you what you need.
```

cd Desktop/package_name
./configure
make
sudo make install

```

If you can use winzip you can use archive manager. *open>extract>location*

---

### Post by munch3 on 2008-02-21
> **3rdalbum said:**
> [www.getdeb.net](www.getdeb.net) has good packages.

But I'd suggest you buy the latest issue of Linux Format magazine, the one with "Distro Heaven" on the cover. They have an ingenius solution to getting packages (and all the dependencies) for one Ubuntu computer, from another computer with an internet connection.This ones good

---

