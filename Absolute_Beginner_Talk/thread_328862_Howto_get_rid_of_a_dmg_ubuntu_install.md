---
title: "Howto get rid of a dmg ubuntu install?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2006-12-31
Hi, 
i had to install ubuntu 2 times till it worked.
Now i can still see the first install filled under other operating systems.

How can i delete this? Is it enough to delte it from the boot loader?


Thx

---

### Post by michaeljustman on 2006-12-31
Just delete it from your /boot/grub/menu.lst to get it to stop showing up.

```
sudo gedit /boot/grub/menu.lst
```

Scroll all the way to the bottom and find the entry you don't want and delete it.

Be careful you don't delete the wrong thing. Maybe backup menu.lst before you start, so you can restore it from a LiveCD or something.

---

### Post by Hendrixski on 2006-12-31
You mean...there are two partitions on the computer, each with an install of Ubuntu, and only one of which works?  If you don't know then you should check withthe LiveCD... open  QParted and see if you don't have two partitions, If so, delete the one you don't want and reallocate that space to the one that works... :)

---

### Post by shareMenaPeace on 2006-12-31
Thank you guys,
it was at the bottom and in fact it is another partition. I will check later with qparted.

---

