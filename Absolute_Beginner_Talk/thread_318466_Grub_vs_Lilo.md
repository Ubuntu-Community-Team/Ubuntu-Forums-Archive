---
title: "Grub vs Lilo"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by computec on 2006-12-14
Grub vs Lilo

What is the pros and cons of both?
What is the real difference?
Which should I use?

Thanks

Alan

---

### Post by bernied on 2006-12-14
I think you'll find most people have only used one of these, so you might not be able to get an objective comparison. I have only ever used grub and recommend it.
pros:
- can boot anything
- is self contained, basically a mini operating system
- very configurable
cons:
- speaks its own language, so not easy at first
- not very pretty

But, if you are using a distribution, the easiest thing to do is to use the boot loader of that distribution, so when using ubuntu, use grub.

---

### Post by md5 on 2006-12-14
[SIZE=2]You can talk a lot about that, but real answer is grub.[/SIZE]

---

### Post by moshuptrail on 2006-12-14
Lilo does "look" nicer.  But Grub is way easier to configure.
With Lilo you have to change the boot file (equiv of menu.lst) and then run a little utility to make the new config available to Lilo.  I could never remember the name of the little utility when I was using Lilo.

---

### Post by computec on 2006-12-14
Thanks guys... I'm useing grub right now since that was what the distro came with.
I guess there really not much difference between them than.


Thanks,


Alan

---

