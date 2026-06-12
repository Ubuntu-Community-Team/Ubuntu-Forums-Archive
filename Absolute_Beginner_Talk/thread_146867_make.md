---
title: "make?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-03-19
im trying to install gimpshop because i like gimp, hate the interface. I cant seem to find a compiled version so have decided to attempt my first app compile.

Stiffed at the first hurdle however trying to install XML pearl parser, it asks where is your make file. Ive tried locatiing it and cannot find it anywhere.
I think its a command as later in the instructions i can see a command:
make install

do i need to get it from somewhere, what is it (i assume its a compiler) and whywhywhy is it always so hard to install anything on linux.(thats not in the synaptic of course :)

---

### Post by KansasJoe on 2006-03-19
you know there's a deb file for that program right?

Found a page which walks you through the install [http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/)

If you need make then sudo apt-get install make

---

### Post by Sef on 2006-03-19
To compile you need to download build-essential first:

sudo apt-get update

then

sudo apt-get install build-essential

---

### Post by dgrafix on 2006-03-19
thanks, that explains a lot.

:)

---

