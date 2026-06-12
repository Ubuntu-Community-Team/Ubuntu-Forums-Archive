---
title: "[SOLVED] problems with Flash Drive"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by WarholsGhost on 2007-07-28
I have a flash drive that is shared between myself and my girlfriend between our two linux computers (both ubuntu) yet the flash drive does not let me change anything and only allows documents to be opened in a read-only format.

how can i make the flash drive be open to wherever it is pluged in?

---

### Post by paradoc on 2007-07-28
lock/unlock micro-switch?..I've got one of these too!

I've also got a similar one that stays permanently locked  that I cannot edit at all

---

### Post by WarholsGhost on 2007-07-28
sudo chmod 777 /media/usbdisk


that helped where usbdisk is where your flash drive is mounted

---

