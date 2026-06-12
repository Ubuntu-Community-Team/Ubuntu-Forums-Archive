---
title: "delete doesn't work"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by NewAgePirate on 2005-11-26
I just noticed that when I delete files there is no more disk space freed up. Do you guys know why that is? I tryed emptying the trash and I looked for a hidden .trash file in the directory (as root), but still no luck freeing up space.

I am currently experimenting with dvdrip and that's why I'm running out of space so fast. Any ideas would be very much appreciated.

Thanks.

~Chloe

---

### Post by crispingatiesa on 2005-11-26
if you deleted the files as root they will go to root's .trash not into /home/username/.trash

so, if you have a root account, check /root/.trash

---

### Post by gord on 2005-11-26
are you just right clicking on the trash icon and pressing 'empty'? if for some reason a file can't be removed from the trash (not got privilges or whatever), it won't return an error. 

your actual trash should be in /home/username/.Trash so try looking about in there. if the files are on a diffirent drive there is a chance they could be in <driveroot>/.Trash

also, if you used root to delete the files they might be somewhere else, allthough in all honisty im not sure ;) somewhere simple though.

are you sure dvdrip is even deleting the files? maybe its leaving them where they are.

---

### Post by NewAgePirate on 2005-11-26
[QUOTE=crispingatiesa]if you deleted the files as root they will go to root's .trash not into /home/username/.trash

so, if you have a root account, check /root/.trash[/QUOTE]

YEAH! That freed up like 10GB! Thanks a bunch! :D 

~Chloe

---

