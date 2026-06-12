---
title: "Problem during ./configure"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-02-22
I'll start off by saying I have ran "sudo apt-get install build-essential" already:

I was trying to build the gtk-qt-engine.  I untared the file, cd, and ran ./configure.  But recieved an error after completion so I couldn't run make or make install (I would post the config.log, but it is wicked long).  Any ideas how I can resolve the problem?  Thanks!

---

### Post by gord on 2006-02-22
reeeeally can't help unless you post some sort of error ;) 

you can get that from the repositorys by the way.
```

sudo apt-get install gtk2-engines-gtk-qt

```
or search for gtk2-engines-gtk-qt in synaptic.

---

### Post by o_fortuna on 2006-02-22
[QUOTE=echo $USER]I'll start off by saying I have ran "sudo apt-get install build-essential" already:

I was trying to build the gtk-qt-engine.  I untared the file, cd, and ran ./configure.  But recieved an error after completion so I couldn't run make or make install (I would post the config.log, but it is wicked long).  Any ideas how I can resolve the problem?  Thanks![/QUOTE]
It's easiest if we can see the log. Instead of posting it, you can compress it (.tar.gz using Applications-->Accessories-->Archive Manager) and upload it as an attachment.

The chances are that you need some "package**-dev**" files that you can install with apt-get. If you look at the log yourself, you will probably see them, although you can feel free to attach it still if you need help.

---

### Post by echo $USER on 2006-02-22
Here is my config.log file.  Thanks for the help.

---

### Post by gord on 2006-02-22
you need the qt dev files 
prolly either libqt4-dev or libqt3-mt-dev 

you can install them via the repositorys

---

### Post by echo $USER on 2006-02-22
[QUOTE=gord]you need the qt dev files 
prolly either libqt4-dev or libqt3-mt-dev 

you can install them via the repositorys[/QUOTE]
I passed the libjpeg check with this package libqt4-dev.  Then failed when checking for Qt.  Installed libqt3-mt-dev, passed Qt check, but now it fails when "checking for KDE... ( I don't have KDE installed ) configure: error: no KDE headers installed. This will fail."  Will installing KDE (but I don't like it) solve my problem?

---

### Post by echo $USER on 2006-02-22
I installed kdedsk.  ./configure finished succesfully as well as make and make install.  Thanks for all the help.

---

