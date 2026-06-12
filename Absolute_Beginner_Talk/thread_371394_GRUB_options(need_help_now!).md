---
title: "GRUB options(need help now!)"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by rabid9797 on 2007-02-26
so im install Dreamlinux on hdb2 on my computer(hd1,2 i think?), and i have the option of install GRUB, not installing it, or installing GRUB to the root partition of this drive. 

so my question(which i need answered now!) is: Can i configure the menu.lst in ubuntu to boot dreamlinux?(and if so, how would i go about doing it?)

---

### Post by rabid9797 on 2007-02-26
ok so im going to go witht he "don't install grub" option, but i still need to know how to modify the menu.lst in ubuntu so that i can boot dreamlinux.

TAURUS! can you help me out with this please? :(

---

### Post by bodhi.zazen on 2007-02-26
LOL

Install GRUB to the (dream linux) root partition.

Boot Ubuntu

edit /boot/grub/menu.lst

Add a stanza for dream linux :

> title Dream Linux
root (hdx,y)
savedefalut
chainloader +1

Note : root (hdx,y) is the dream linux root partition in grub speak ...

Note : When you boot Dream you will get a second grub screen. If this is working, edit, on the dream_root /boot/grub/menu.lst and change

default 0
timeout 0

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by rabid9797 on 2007-02-26
aw crap, i alrady said no grub and finished installation. :lol: i guess i'll just go back and reinstall.

thanks for the help

---

### Post by rabid9797 on 2007-02-26
EDIT: nvm i had wrong partition number :lol:

---

### Post by bodhi.zazen on 2007-02-26
LOL

So are you up and running ?

---

