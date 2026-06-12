---
title: "Where to get Programming software for Ubuntu?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by chathu03j on 2007-05-23
Hi, I'm quite new to using ubuntu.
I have installed Ubuntu using a CD and I want to install programming software. I know that when u install Fedora they ask you if you want to install Programming s/w and give u the option to do so. How do I do that in Ubuntu? Are the s/w available on the CD or do I have to download them? How should I install when I get them?

Thankls for any reply!!!

---

### Post by Rinzwind on 2007-05-23
Hello.

Python should already be installed (type
python 
in command line).

Gnome also has a programming menu. Look in "ADD/REMOVE programs" to see a limited list of editors, coding software etc etc.

---

### Post by Celegorm on 2007-05-23
You'll want to install the build-essential package, which includes various compilers and such. To do this type
```
sudo apt-get install build-essential
```in the command line. It will ask for your password, type it and hit enter.

If you want an integrated development environment, I suggest looking in [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

