---
title: "how to install on mac mini"
date: 2007-12-21
forum: Apple Intel Users
---

### Post by brandon333 on 2007-12-21
want to partition drive, in disc utility i see where i can make it into two, so my questions are:

how many partitions should i make for ubuntu and osx leopard, 1 for each right?

once that is done, i will put in the live cd, what button do i push to boot from cd?

then once in the install (been there before) i always get lost on which to pick, manual install or what?

when i did it before i kept getting errors saying i must make a swap, etc.

i have an intel mac mini 1.83, just bought it.

---

### Post by brandon333 on 2007-12-21
anyone?

the live cd will not load, how do iboot from cd, what button?

---

### Post by cyberdork33 on 2007-12-21
> **brandon333 said:**
> anyone?

the live cd will not load, how do iboot from cd, what button?
hold c

---

### Post by DGortze380 on 2007-12-21
> **brandon333 said:**
> want to partition drive, in disc utility i see where i can make it into two, so my questions are:

how many partitions should i make for ubuntu and osx leopard, 1 for each right?

once that is done, i will put in the live cd, what button do i push to boot from cd?

then once in the install (been there before) i always get lost on which to pick, manual install or what?

when i did it before i kept getting errors saying i must make a swap, etc.

i have an intel mac mini 1.83, just bought it.

You need 3 partitions, OS X, Ubuntu, Swap (swap needs to be formated as swap and should be double the amount of RAM you have). It works like Virtual Memory in Windows.

hold either c or option to boot from a cd

manual install, it will let you select and format partitions so you don't overwrite OS X. You need a root "/" partition and swap for ubuntu to install.

---

### Post by brandon333 on 2007-12-21
if i could find the partition editor I could screen print and show you what I have, but the partition editor is no longer in preferenses.

---

### Post by DGortze380 on 2007-12-22
> **brandon333 said:**
> if i could find the partition editor I could screen print and show you what I have, but the partition editor is no longer in preferenses.

are you using a live cd? open a terminal and type 

> sudo gparted

If it tells you it's not installed (it should be if you're on a live cd), type 

> sudo apt-get install gparted

---

### Post by brandon333 on 2007-12-22
had to uninstall kubuntu, was causing way to many issues anyhow got gparted back and here is a screenshot

---

### Post by DGortze380 on 2007-12-22
ok, partition scheme looks normal, but I'm confused here.  what exactly are you trying to install? it looks like you already have a version of ubuntu up and running...

idk, w/e....

to install, boot from the live CD, hold alt or c to do so.  Double click install on the desktop. Select manual install when prompted, Mark sda3 as root >  /  and sda4 as swap >  linux-swap .

Side note, you don't really need to leave that space between partition in the future.

---

