---
title: "Micro sd disk full"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by BodaciousBrian on 2007-12-20
When trying to copy files to my micro sd card nautilus  says the disk is full.  At the same time,  nautilus says the disk is about 1/2 full when i right click and look at the properties on the disk, and on the bottom of the nautilus screen it says "131 items, Free space: 428.6 MB"

Ive tried using the disk while its in my mp3 player, and while its plugged directly into the usb.  Both ways give the same result.

---

### Post by IanW on 2007-12-20
Try emptying your trash can.
Then look at the card in Nautilus again and press "CTRL-H" to show any hidden files.

If neither of the above work, then copy everything OFF the card & re-format it.

---

### Post by BodaciousBrian on 2007-12-20
Reformatting using ":confused:sudo mkdosfs -F 16 /dev/sda1" worked.  I did reformat the the thing in windows, and that didn't!  Thanks for the help.

---

