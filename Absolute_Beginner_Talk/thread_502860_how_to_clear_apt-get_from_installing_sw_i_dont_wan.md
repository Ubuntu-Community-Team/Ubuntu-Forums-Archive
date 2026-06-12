---
title: "how to clear apt-get from installing s/w i dont want"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-07-17
i installed a ton of fonts in one hit and some of them needed JAVA installed so i declined as im paranoid about java scripts.

now i have managed to sort of screw up Ubunto Fiesty a bit.
now if i run the updade program i get this error

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

if i fire up the termial and do the sudo apt-get install -f

it wants to try and reinstall the java programs, about 4 in total.
how do i clear the from the apt-get function?

---

### Post by meborc on 2007-07-17
install the java packages using "sudo apt-get -f install"

then remove them with "sudo apt-get remove <package> <package2>..." this will also remove the fonts that depend on java...

now you should have a stable system

---

### Post by stinger30au on 2007-07-17
ok, thanks.
just thought there may have been a modifer or switch i could use to clear it.
will install then uninstall

---

