---
title: "rEFIt not working with OSX 10.6.1?"
date: 2009-09-21
forum: Apple Hardware Users
---

### Post by Aybara on 2009-09-21
I plan to have a Karmic / Snow Leopard dual boot, and I just installed rEFIt. Much to my dismay I didn't get the rEFIt menu when I restarted my Mac (after a real shutdown). Anyone know how I can fix this?

---

### Post by digitaladdictions on 2009-09-22
It works for me in 10.6.1.

cd /efi/refit
./enable.sh

---

### Post by Aybara on 2009-09-22
Thanks. After I held 'C' on a reboot it started working here as well.

---

### Post by Aybara on 2009-09-23
But the joy didn't last.

I have installed Karmic now, but something is not right.

When I boot, rEFIt shows me three options. 

1. OS X. This works.
2. "Boot Linux from HD". If I choose this I get a grub command line
3. "Boot legacy os from /dev/sda3". If I choose this, nothing at all happens. /dev/sda3 is where I installed Grub (like the install wiki on this forum says I should)

If I choose the Partition Tool in rEFIt, it discovers something unknown and won't touch the partition table (don't remember the exact error just now).

---

### Post by GadgetFreak on 2009-09-23
> **Aybara said:**
> But the joy didn't last.

I have installed Karmic now, but something is not right.

When I boot, rEFIt shows me three options. 

1. OS X. This works.
2. "Boot Linux from HD". If I choose this I get a grub command line
3. "Boot legacy os from /dev/sda3". If I choose this, nothing at all happens. /dev/sda3 is where I installed Grub (like the install wiki on this forum says I should)

If I choose the Partition Tool in rEFIt, it discovers something unknown and won't touch the partition table (don't remember the exact error just now).


I cannot address your specific issue (I have very little experience in this area) but I can tell you that rEFIt works fine on my Mac Mini with 10.6.1. I upgraded to Snow Leopard (and then applied the update to 10.6.1) before partitioning the internal HD, installing rEFIt, and then installing Ubuntu 9.04 server on that new partition. My Grub installation went to the same place as yours (/dev/sda3). Since then I've used the "Mac side" quite a bit without issue although I only dabble on the Ubuntu side. All seems fine.

---

### Post by Aybara on 2009-09-24
The partitioner must work differently in Karmin than in Jaunty, because when I went back to Jaunty it worked. I still have one penguin too much in my rEFIt menu, but as long as I can get to both OS X and Ubuntu I'm happy :)

---

