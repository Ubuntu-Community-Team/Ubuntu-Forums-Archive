---
title: "has any mac users managed to install Cedega"
date: 2005-04-12
forum: Apple PPC Users
---

### Post by ninjag5 on 2005-04-12
title says it all 

i want to know if you have managed to installed Cedega(wineX) on your mac running Ubuntu Linux 

if you have how did you do it?

---

### Post by godsunderstudy on 2005-04-12
I'm almost certain it's impossible. Cedega is an extension to WINE, and WINE is x86 only.

---

### Post by ninjag5 on 2005-04-12
yeah im sure ur right it wouldnt let me so i think if i get Ubuntu on a pc ill try it then

---

### Post by ssam on 2005-04-13
you would have to emulate an x86 (eg pentium amd) processor.

this can be done but is slow, each processor instruction needs to be translated as the program runs.

qemu can do the emulation, but it has not been tied into wine (yet), look up the darwine project.

you could use qemu to to boot the x86 version of ubuntu in a virtual machine and then run wine/cedega in that, but if you want to run games this will be slow.

---

