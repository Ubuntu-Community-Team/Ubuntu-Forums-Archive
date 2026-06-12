---
title: "Xmms VUmeter"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Fred_E _krugar on 2007-09-22
I have tried several times to install the vumeter plugin for xmms.  At the end it tells me that glib 1.2.1 not installed .

  I went and got the glib tried to install; it gets to the very end of Make Install then gives me an error ; Leaving directory ,WTF am I doing wrong???

---

### Post by Fred_E _krugar on 2007-09-22
No takers huh?????

---

### Post by kitcorey on 2007-11-19
I had to install the development glib package for it to compile

sudo apt-get install libglib1.2-dev

I also had to install pixbuf dev

sudo apt-get install libgdk-pixbuf-dev
 
Good luck

---

