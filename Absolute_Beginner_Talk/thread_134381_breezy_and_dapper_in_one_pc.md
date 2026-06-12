---
title: "breezy and dapper in one pc"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by widjajayd on 2006-02-21
Can I install breezy and dapper in one pc.
currently in my pc I use multiboot dapper and windows XP

I want to install breezy also, if yes when I install breezy 
what is major question that enable me to do this.:-k 

Thank you all for great support

widjajayd

---

### Post by AndyCooll on 2006-02-21
It shouldn't be a problem. You just need a spare partition to install Breezy to.

:cool:

---

### Post by hoodwink on 2006-02-21
[QUOTE=widjajayd]Can I install breezy and dapper in one pc.
currently in my pc I use multiboot dapper and windows XP

I want to install breezy also, if yes when I install breezy 
what is major question that enable me to do this.:-k 

Thank you all for great support

widjajayd[/QUOTE]
The simple answer is yes, no problem. You can have as many multi-boot systems as you have disk space for additional systems. The installer will allow you to do this, and it will detect and make available for boot all your systems.

Now the questions:

1) Have you used all the space on your drive with your Windows/Breezy setup?

If the answer is no, and you have at least 3-5Gig free space left, just crank up a Dapper install dist and tell it to create a new partition or partitions to install Dapper. When you complete the install, Dapper will be the default boot choice, but Breezy and Windows will be further down the grub menu list.

2) If the answer is yes, consider installing a second harddrive. There are methods to shrink the size of your existing partitions, but this action is a little beyond beginner level. If you add a new harddrive, you can install just as described above.

HTH,

---

