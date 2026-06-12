---
title: "setup.sh"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by rwilmink on 2006-02-04
Hi all,

I have a problem that someone can hopefully help me with: I have a few programs on cd, like Railroad Tycoon 2, Simcyty 3000 etc, that have a setup-script setup.sh.
I cannot run this script, because I have a ' bad interpretor' >> permission denied.
These scripts worked on RedHat.

How do I install these?

---

### Post by Pragmatist on 2006-02-04
type: cat setup.sh

cut & paste this to the screen.  Or, if you want to attach it as a file type:

cat setup.sh > yourfile

Also, are there README files and INSTALL files in the directories corresponding to those games??

At the most basic level, you might need to download certain libraries or language interpreters.

---

### Post by kingsidy on 2006-02-05
in order to run that, type in at the command line:

> sudo sh install.sh

---

### Post by rwilmink on 2006-02-05
sudo sh setup.sh did the trick!

Thanks.

---

### Post by Knight.Watchman on 2008-02-04
I have a different issue with the same file.
I am attempting to do a new install from the CD Rom.
This is a new installion of Ubuntu 7.10.
from the /media/cdrom0
sudo sh setup.sh

error...
setup.sh: 9 finction: not found
x86

I am sure it must be something I overlooked, since I have not had problems installing this in the past.
(This is for RailRoad Tycoon II)

---

### Post by Knight.Watchman on 2008-02-04
Found the answer here.
[http://ubuntuforums.org/showthread.php?t=402777](http://ubuntuforums.org/showthread.php?t=402777)
Thanks!!

---

