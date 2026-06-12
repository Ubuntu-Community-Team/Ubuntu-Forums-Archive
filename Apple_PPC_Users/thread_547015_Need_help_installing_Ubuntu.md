---
title: "Need help installing Ubuntu"
date: 2007-09-09
forum: Apple PPC Users
---

### Post by varial8kickflip on 2007-09-09
i am new to this kind of thing but.. I really want to have two operating systems (mac on linux) but when i install ubuntu i am unable to have mac. How would i be able to have both (i know there are answers out there but there are complicated so could someone write a noob friendly one for me)?
Thanks

---

### Post by Auria on 2007-09-10
Hi,

it would help to know what install steps you followed, as there are 2 alternatives : either you install ubuntu over OS X, either you install ubuntu in its partition but the boot loader doesn't know aboutOS X.

general instructions :

you will want to install mac OS X first on your computer. I don't know what is your computer, but i'll assume you can boot tthe liveCD. Once on the ubuntu liveCD, search the utility menus for the partitioner. Use it to shrink your OS X partition (back up any important data before) and leave the remaining space empty (no partiton) Then use the installer and tell it to install in the largest free space when you reahc he step where it asks where to install.

When you boot, it will probably show a screen where it asks whether you want to boot in ubuntu or os x.

If it doesn't, boot with alt down and yu can use OS X too. You could also configure yaboot to see OS X but  dont know how to do that myself.

---

### Post by varial8kickflip on 2007-09-10
Thank you so much i have finaly done it

---

