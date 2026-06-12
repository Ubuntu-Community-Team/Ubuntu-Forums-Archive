---
title: "Dual boot ubuntu and Vista"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by j_o on 2008-03-25
I currently have windows vista home premium installed on my computer. I have a guide on how to dual boot but my computer has to hard drive. What I was planning to do was shrink the partition that my vista is using and then use the guided hard drive choser in the linux installation. My question is how do I make sure that it chooses that unpartiioned space and does not touch the second hard drive.

---

### Post by JawsThemeSwimming428 on 2008-03-25
When installing Ubuntu, you would have to explicitly select the exact partition you want to use. For example:

 If you have three partitions

   sda1 - Free partition for Ubuntu
  
   sda2  - Let's say this is your Vista partition

   sdb1 - Second HDD

 You would have to select sda1 when installing and it will leave the other partitions alone. (I have never had an issue with the Ubuntu installer, but it is still a good idea to back all data up on any partition). Hope this helps!

---

### Post by knightcoder on 2008-03-25
The ubuntu installer gives you an option to select the size you want to use on your primary partition. I think you can also select from the end of the partition (the free space on the end).

Also, the second drive would be named differently. So, you can distinguish between the two.
If you can't by the name, check the size of the drives ( size of used space) which may be an indicator.

---

