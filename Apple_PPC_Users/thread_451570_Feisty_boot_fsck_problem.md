---
title: "Feisty boot fsck problem"
date: 2007-05-22
forum: Apple PPC Users
---

### Post by mrqwa on 2007-05-22
i´ve solved some boot errors, and now.. 
my screen on boot goes like this::

> * Activating swap
* Checking root file system…
fsck 1.40-WIP (14-Nov-2006)
/dev/hda3: clean, 218730/4931584 files, 9239843/9849609 blocks

* Checking file systems…
fsck 1.40-WIP (14-Nov-2006)

and then... nothing. boot stops.
i don´t understand....... thanks a lot

sometimes are there also lines like this
> udevd[1945]: init_udevd_socket: bind failed: Address alredy in use
udevd[1945]: main error initializing udevd socket
findfs: unable to resolve 'UUID=0fb34b7-b59b-4855-od80-621c55714fd7'

and in my /etc/fstab i found this line:
> #dev/hda3
UUID=0fb34b7-b59b-4855-od80-621c55714fd7   /  ext3   defaults, errors=remount-ro 0 1

can you help me please?

sorry for my bad english

---

### Post by mrqwa on 2007-05-28
no anwsers??
:-(((

---

### Post by stmiller on 2007-05-28
What kind of computer is this?

Sounds like you possibly have some bad sectors on your hard disc. You can boot the alternative CD into 'rescue mode' which has checks for the hard disc and may be able to fix it.

---

