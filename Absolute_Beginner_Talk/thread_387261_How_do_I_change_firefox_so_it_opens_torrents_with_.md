---
title: "How do I change firefox so it opens torrents with Azureus"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Hortinstein on 2007-03-18
I do the thing with the download, but i cant find azureus anywhere...im a little new to the way linux filesystems are structured

---

### Post by AtrejuT on 2007-03-18
for me it is in /usr/bin/azureus, but you should not need the complete path. If you can just tell it to execute 'azureus' without the quotes everything should work.

atreju

---

### Post by Hortinstein on 2007-03-18
awesome...really appreciate it

---

### Post by Kateikyoushi on 2007-03-18
Azureus is in /ussr/bin.

---

### Post by Goodson1974 on 2007-03-18
Hi

Just looked in usr/bin and there's no sign of Azureus.
I installed it with Automatix2.  Does this put it somewhere different?

---

### Post by Dirty Ole on 2007-03-18
in terminal type "locate azureus" without the quotes. You will get its location.

Also right click on a .torrent file and select azureus as the default file handler.

---

### Post by Goodson1974 on 2007-03-18
That's brilliant!

Thanks for that :)

---

### Post by Efros on 2007-03-18
Azureus has a watch folder feature, save your torrents to your usual download directory, have azureus monitoring that directory for new torrents.

---

### Post by TheVeech on 2007-03-25
You can also edit:
mimeTypes.rdf
in the (hidden: /home*/loginname/*.mozilla) .mozilla subdirectories

---

