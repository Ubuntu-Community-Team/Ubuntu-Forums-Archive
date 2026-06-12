---
title: "Hu?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-04-24
hi, i did the big miss of installing Ubuntu 64 bit edition, so i have downloaded the 32 bit edition dvd and wan't to install it.  But i can't edit/delete anny partitions, i want to delete the extended partition. 
[[img]http://bildr.no/thumb/59351.jpeg[/img]](http://bildr.no/view/59351)

Look at the picture

---

### Post by ajmannen on 2007-04-24
I tried to unmount the partitions, but i still can't delete the partition i want

[[img]http://bildr.no/thumb/59354.jpeg[/img]](http://bildr.no/view/59354)

---

### Post by LaRoza on 2007-04-24
Use the GParted Live CD, it will probably work.

---

### Post by pppetter on 2007-04-24
You'll probably need to delete the partitions that are inside the extended one first - sda5 and sda6. 

And hey, you could always install on sda5....

---

### Post by mangoti on 2007-04-24
You will first have to delete the two partitions inside the extended partition. This means that you will have to turn the swap partition off. I think ```
swapoff /dev/sda6
``` should do the trick. But depending on its specs, your system can become irresponsive if swap is turned off.

---

