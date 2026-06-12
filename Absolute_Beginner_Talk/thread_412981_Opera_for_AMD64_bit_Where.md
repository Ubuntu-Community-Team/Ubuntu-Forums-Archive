---
title: "Opera for AMD64 bit? Where?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by dibbz on 2007-04-18
Where can I find a 64bit version of the latest Opera browser? I can see the 32bit version in the Synaptic Package but I can't install it because it is 32bit. Wierd because I though that I still might have been able to even though I have the 64bit version of Edgy.

---

### Post by JayTheHun on 2007-04-18
There doesn't appear to be such a version:  [http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by dibbz on 2007-04-18
So is there no way to get Opera running on my 64bit Edgy?

---

### Post by igknighted on 2007-04-18
You can install the 32bit package, but it wont run in 64bit mode.  Synaptic probably won't let you do this, so go to the opera site, get the ,deb, and use "dpgk -i --noarch <packagename>" to install

---

### Post by dibbz on 2007-04-18
I tried 

> dpgk -i --noarch opera_9.10-20061214.6-shared-qt_en_i386.deb but it says 
dpgk comman not found.

EDIT:- ok I tried 
> dpkg 
 at the front and am now getting 

> unknown option --noarch

EDIT 2:-  Fixed it.

Installed 32bit libs

> sudo apt-get install ia32-libs ia32-libs-kde lib32asound2

then 

> sudo dpkg --install --force-architecture  opera_9.20-20070409.6-shared-qt_en_i386.deb

---

### Post by igknighted on 2007-04-18
> **dibbz said:**
> Fixed it.

Sorry, I use too many package managers, the syntax get jumbled sometimes :)

---

### Post by Terracotta on 2007-05-05
> **dibbz said:**
> I tried 

 but it says 
dpgk comman not found.

EDIT:- ok I tried 
 
 at the front and am now getting 



EDIT 2:-  Fixed it.

Installed 32bit libs



then
I tried this but I get this after installation when I try to run opera I get this:

```
 terracotta@Hydra:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.20-20070409.6/opera: error while loading shared libraries: libXcursor.so.1: wrong ELF class: ELFCLASS64

```

Is this because I mixed 32bit and 64 bit?

---

