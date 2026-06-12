---
title: "upgrade question"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by NOSintake on 2007-05-12
i currently have ubuntu 6.10, so if i upgrade, will i have to reinstall all my programs like beryl and things like that? also, will i have to redo my video card settings?

ive been out of linux for a month or so, so i have no idea whats going on now. thanks for the help

---

### Post by overdrank on 2007-05-12
> **NOSintake said:**
> i currently have ubuntu 6.10, so if i upgrade, will i have to reinstall all my programs like beryl and things like that? also, will i have to redo my video card settings?

ive been out of linux for a month or so, so i have no idea whats going on now. thanks for the help

Hi from what I have seen in the post then yes to your questions!. :(

---

### Post by trent dillman on 2007-05-12
...

---

### Post by jfinkels on 2007-05-12
> **NOSintake said:**
> i currently have ubuntu 6.10, so if i upgrade, will i have to reinstall all my programs like beryl and things like that? also, will i have to redo my video card settings?

ive been out of linux for a month or so, so i have no idea whats going on now. thanks for the help

Well if you update using the update-manager or aptitude or apt-get, you will just get updates to your programs, you shouldn't have to reinstall them!

If you are concerned, you should make a backup copy of your /etc/X11/xorg.conf file.

---

### Post by [S|G] on 2007-05-12
I didn't have to reinstall any programs (I can't say about beryl since I didn't have it installed before) after my upgrade from 6.10 to 7.04. Even if you have to reinstall beryl your settings will not be lost, though, since it will read your old configuration files.

But if you're using nvidia official drivers (probably ATI as well) you'll most likely have to re-install them, since when you upgrade you'll get a new kernel.

---

