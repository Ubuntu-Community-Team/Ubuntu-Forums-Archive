---
title: "windows have overwritten my boot record"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by smurf killer on 2007-04-06
i came to overwrite my linux boot record with a windows, but how do i make it back so that i have the old boot record?

---

### Post by cypherzero on 2007-04-06
Reinstall grub from ubuntu (use the Live CD if you can't get it started)

In the terminal type:

[COLOR="Blue"]sudo grub-install --root-directory=<GRUB> <DEVICE>[/COLOR]

[COLOR="Blue"]<GRUB>[/COLOR] The path that contains the grub boot folder, eg. [COLOR="Blue"]/boot[/COLOR]
[COLOR="Blue"]<DEVICE>[/COLOR] The device you want to install GRUB to, most likley [COLOR="Blue"]dev/hda[/COLOR]

---

### Post by smurf killer on 2007-04-07
im not sure what drive my linux is installed on. but if i try your example it wont do anything, something about "format of install_device not recognized"

---

### Post by OffHand on 2007-04-07
This guide explains it in an easy way:

[http://johnny.chadda.se/2007/02/17/restore-grub-in-ubuntu-after-installing-windows/](http://johnny.chadda.se/2007/02/17/restore-grub-in-ubuntu-after-installing-windows/)

(You might need to manually add an entry to the grub for Windows again after doing this.)

---

### Post by smurf killer on 2007-04-07
thanks ill have a look at it :)

---

### Post by smurf killer on 2007-04-07
hmm unfortunately it won't mount my drive error: "mount: you must specify the filesystem type" why could that be? tried to copy/paste it

---

### Post by smurf killer on 2007-04-07
> **smurf killer said:**
> hmm unfortunately it won't mount my drive error: "mount: you must specify the filesystem type" why could that be? tried to copy/paste it

never mind that, the error was that i copy/pasted it and it wasn't the correct drive, silly me ;)

---

### Post by OffHand on 2007-04-07
> **smurf killer said:**
> never mind that, the error was that i copy/pasted it and it wasn't the correct drive, silly me ;)

Did it work out for you?

---

### Post by smurf killer on 2007-04-07
yea thanks it did. now it is just some other things that wont work ;)

---

### Post by OffHand on 2007-04-07
> **smurf killer said:**
> yea thanks it did. now it is just some other things that wont work ;)

Alrighty... glad to hear. Best make a separate thread for the new issues. C ya.

---

