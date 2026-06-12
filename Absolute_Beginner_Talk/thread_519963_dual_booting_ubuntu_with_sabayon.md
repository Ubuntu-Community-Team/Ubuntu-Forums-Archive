---
title: "dual booting ubuntu with sabayon?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by threeonethree on 2007-08-07
hi people i just downloaded sabayon linux to give it a try (ubuntu user for past couple of months)

i have made a "/" ext 3 partition for ubuntu  as well as a 1 gb swap.. can you tell me how do i partition for sabayon so that my ubuntu remains intact? i have lots of settings etc on it... can i just make another "/" ext 3 partition for sabayon? i dont think that will work

---

### Post by dougfractal on 2007-08-07
Use the liveCD to repartition the / partion
sudo gparted

**ext3 can be resized while not mounted**

check ubuntu still boots.
Install sabayon on the new partion
use a shared swap.
edit grub/menu.lst so you have ubuntu and sabayon


If you have lots of HD you can do multiple partions. So you can have a linux multiboot and try all the flavors ;)
10-15GB per OS
1 GB swap
shared /home

---

### Post by annda on 2007-08-07
sabayon needs at least 12 GB for install (unless you have the mini edition), so use more if you can. swap can be shared, so you can use the ubuntu one in sabayon, just point to the right partition.

---

