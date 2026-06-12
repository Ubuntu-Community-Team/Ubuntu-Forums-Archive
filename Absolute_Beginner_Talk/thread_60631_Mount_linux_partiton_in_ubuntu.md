---
title: "Mount linux partiton in ubuntu"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-08-28
Hey, how can i mount a linux partiton on my current install of ubuntu, i have my ntfs mounted... but the linux one dosnt want to mount... any help??

Thx
~Lance

---

### Post by manicka on 2005-08-28
[QUOTE=noob_Lance]Hey, how can i mount a linux partiton on my current install of ubuntu, i have my ntfs mounted... but the linux one dosnt want to mount... any help??

Thx
~Lance[/QUOTE]
 Add an entry something like this to your fstab

/dev/hdb9       /mnt/linux     ext3(or however you have it formatted)    defaults        0       2

---

### Post by noob_Lance on 2005-08-28
and where do i find this... fstab??

---

### Post by manicka on 2005-08-28
[QUOTE=noob_Lance]and where do i find this... fstab??[/QUOTE]
 sudo gedit /etc/fstab

Add an entry to suit your drive.

---

