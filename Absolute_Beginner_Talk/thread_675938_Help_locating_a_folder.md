---
title: "Help locating a folder"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by apoch632 on 2008-01-23
I need to find where the <php root>/php/include/php/ext/ folder is.

I need to install rrd tool to this folder.

I know how to install rrd tool but I'm just having trouble locating where the php/include/... folder is

I've installed php5 with the apt-get

---

### Post by philinux on 2008-01-23
If you go back to synaptic and php5 then look at the tab installed files. Always useful to know where things get put.

---

### Post by lgambett on 2008-01-23
Try from the command line a;

sudo find / -name php 2> /dev/null

o

sudo find / -name include 2> /dev/null

(the 2> /dev/null cancels annoying error messages)

---

### Post by apoch632 on 2008-01-23
No luck find the folder

---

### Post by philinux on 2008-01-23
Does it install to

/usr/local/php5

---

### Post by apoch632 on 2008-01-23
It justs lists as follows
 /.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/php5

---

### Post by philinux on 2008-01-23
Look in 

/usr/local   

not share.

---

### Post by philinux on 2008-01-23
Have a look in

/etc/php5/

too.

---

### Post by rustutzman on 2008-01-23
Try 'locate php'

Russ

---

### Post by staticvoid on 2008-01-23
does the 'whereis' command work for this kinda thing?

i'm no extreme terminal power user... i can  cd, ls, cp, mv, sudo and use tp lol... in a terminal....

:)

whereis php


sv

---

