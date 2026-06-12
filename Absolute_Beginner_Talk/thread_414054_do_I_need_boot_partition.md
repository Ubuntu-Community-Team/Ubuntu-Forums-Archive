---
title: "do I need /boot partition?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by medya on 2007-04-19
hey I am gonna re-partition my hard disk and install the Fiesty Faw , 

for re-partitioning of my hard disk, I have some questions , do I need a partition for /boot ? would it make my ubuntu faster?  how big the /boot partition should be ?

my other question is , would putting swap partition in the Begining of the hard disk make it faster ?
like

swap
boot
root
home

I alway heared  the partitions in the first are accessed faster . 
I am also gonna give Swap , space 3 times more than my ram .
is it a good idea?

---

### Post by lamalex on 2007-04-19
how much ram do you have? you don't really need 3 times your ram probably, 1 to 2 times is plenty, i never swap as it is. as for /boot, you don't need to make it but it helps boot faster specially if you do it as ext2 fs. if yu dont make it, it's included in /(root)

---

### Post by medya on 2007-04-19
my ram is 256, you didnt tell me how big the Boot partition  should  be?

---

### Post by eyelessfade on 2007-04-19
you don't need boot but it is recomended. Mine is 100MB that is more then enough. But you will get in trouble if you have to many kernels at the same time.

---

