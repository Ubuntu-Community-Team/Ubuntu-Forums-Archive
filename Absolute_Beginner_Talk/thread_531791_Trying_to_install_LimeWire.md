---
title: "Trying to install LimeWire"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Just-trevor on 2007-08-22
I installed the package but its not a rpm file its a deb file...
when I put it in the limewire folder I made it didnt have the file it should have had
what did I do wrong???

---

### Post by sumguy231 on 2007-08-22
It would be nice to get a little more detail on the error output you're getting, but it sounds like you didn't have all the dependencies to install Limewire. Look at the packages it requires and try installing them with Synaptic.

---

### Post by dpar on 2007-08-22
Have you tried Frostwire??

PS to sumguy.....are you the same sumguy from Firefox forums??

---

### Post by swoll1980 on 2007-08-22
run "sudo apt-get install -f " see if that clears it up. The file you are downloading is supposed to be a .deb not .rpm (no quotes in the run command)

---

### Post by sumguy231 on 2007-08-22
> PS to sumguy.....are you the same sumguy from Firefox forums??
Yea, but I changed my username. I'm "Tad Ghostal" now.

---

### Post by Jimmyfj on 2007-08-22
You can download the Limewire installer directly from their website:

[http://www.limewire.com/download/download.php?version=linux_deb](http://www.limewire.com/download/download.php?version=linux_deb)

Just save the file and browse to it. Dbl-click on the file and use the debian installer that pops up. This will get the files you need automatically.

---

