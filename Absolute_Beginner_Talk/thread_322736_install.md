---
title: "install"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2006-12-20
I am new to linux

How do I install in the command Line???

---

### Post by meng on 2006-12-20
What are you trying to install?

---

### Post by jem7v on 2006-12-20
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html) has the instructions from the Ubuntu Desktop Guide.  They're pretty straight forward.

---

### Post by RED WIND on 2006-12-20
xfire add on for gaim but I would like to know hoe to install other things too

I already know about (sudo make install)

---

### Post by jem7v on 2006-12-20
Well I think that particular plugin just installs from a .deb file, so go to the directory it's in and use this command to install the package.

sudo dpkg -i package_file.deb

If you want to remove it later, use -r instead of -i, and leave off the .deb extension.

---

### Post by meng on 2006-12-20
There are .deb packages downloadable
[https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388](https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388)
assuming you use breezy or dapper i386.

Otherwise, you'll have to install from source:
download the .tgz
and then follow the instructions for installing from source:
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
(section 4)

---

### Post by r4ik on 2006-12-20
Here's a read about installing,

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Good luck !

---

