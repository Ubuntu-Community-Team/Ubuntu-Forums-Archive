---
title: "[SOLVED] Killed Winders and need to kill boot options"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Dedman on 2007-06-18
I have used GParted to repartition my HD and remove Windows. After searching in vain, possibly just using the wrong phrases, I cannot find how to remove the dual-boot option. ](*,) I changed my /boot/grub/menu.lst to have a 0 sec timeout. But I was interested in finding a removal if at all possible. 

DEDMAN

---

### Post by Cypher on 2007-06-18
Edit the file /boot/grub/menu.lst and scroll to the bottom. You will see the Windows XP option there, remove that from the list. Uncomment the "Hiddenmenu" option and keep the time at at least 5 seconds in case you need to use the "Recovery" Kernels for whatever reason.

With a timeout of 0 seconds, you will be stuck if your regular Kernel fails..

---

### Post by Dedman on 2007-06-18
Thanks. I pretty much had that already, but I just was unsure if the GRUB was always there. Both my desktop and laptop were dual boot, (wife loves windows). I do appreciate he help.

Dedman

---

### Post by steve.horsley on 2007-06-18
GRUB is always there and always needed. You can set the timeout really short if you like.

---

