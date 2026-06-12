---
title: "Can't make distclean?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2006-08-21
My wireless card is (no surprise) not being detected, so I figured the easiest way to fix this is to install ndiswrapper (as it's worked quite well for me on knoppix). I've expanded the tarball and this happens:

cedric@cedbuntu:~/Downloads$ tar zxvf ndiswrapper-1.23.tar.gz
...
cedric@cedbuntu:~/Downloads/ndiswrapper-1.23$ make distclean
bash: make: command not found

Am I missing this incredibly useful command? What do I do?

---

### Post by Fass on 2006-08-21
Have you installed build-essential?

---

### Post by byen on 2006-08-21
The most easiest way to install ndiswrapper via ubuntu would be to use the Ubuntu/kubuntu CD.  Just pop in the CD > Open Synaptic>  Edit>Add CDROM and search for the package named "ndiswrapper-utils" and select to install.
Hope this is the solution you are looking for... Goodluck!
regards,
byen

---

