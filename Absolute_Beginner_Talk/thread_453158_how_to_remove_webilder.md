---
title: "how to remove webilder"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by zorro26 on 2007-05-24
hi, i have installed webilder, which automaticly changes desktop background, but i dont like it cause you have no control what pics you wand and they dont fit desktop properly. it only shows half pic or so.. and there is no option to set it right.

i want to remove this program, i searched forums, tred readme but no instructions how to uninstall. can some one pls help me.

i ahve installed it as following

> # apt-get install python python-gtk2-dev python-gnome2 python-gnome2-dev \
        libglib2.0-dev python-gnome2-extras python-gnome2-extras-dev \
        python-imaging
tar xzf Webilder-0.6.2.tar.gz
$ cd Webilder-0.6.2
$ su
Password:
# python setup.py install

---

### Post by zorro26 on 2007-05-24
**can i uninstall it**

---

### Post by Viskovitz on 2007-05-24
I've looked at the installation script and it has no "remove" option. Maybe you can erase all the related files by hand, but it's not a very elegant way. To do this:

```
whereis webilder
```

if the output is, say, /usr/bin/webilder, you can:

```

sudo rm /usr/bin/webilder
rm -rv ~/.webilder

```

Next time use the repositories, as they suggest in the webilder site.

---

### Post by zorro26 on 2007-05-24
> rm -rv ~/.webilder worked but... get this error

> root@kal:~# sudo rm /usr/share/webilder
rm: cannot remove `/usr/share/webilder': Is a directory

---

### Post by bobplano on 2007-05-24
you can force it to remove
```
sudo rm -rf /usr/share/webilder
```
you need the tags to remove the folder

---

### Post by zorro26 on 2007-05-24
that did the job,,,,, thanks alot

---

