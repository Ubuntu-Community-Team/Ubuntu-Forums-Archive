---
title: "install problem with partitions"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by cdssf on 2007-02-24
Hi, I am brand new to this and got stuck early.  I am trying to install and am at the partition stage.  Windows has three partitions on my hard drive and I was able to create a forth using Gparted.  I know I need another for Swap and that I am limited to four primary.  I saw that Swap does not have to be primary--it can be logical.  I see no way at all to create another partition, logical or otherwise.  All Gparted will let me do is resize any of the four.

Sorry if this is a dumb question but I'm no expert at this stuff (to put it mildly) and just cannot get past this point.  How do I create a fifth partition for Swap?

Thanks very much for your patience.

---

### Post by taurus on 2007-02-24
Why not make the 4th one, the one that you intend to install Ubuntu on, as an extended partition and the installer will know how to create two logical partitions, one for / and one for swap, from that.

---

### Post by yabbadabbadont on 2007-02-24
Change the type of the partition that you created to be Extended.  Then you should be able to create the logical partitions you need within that Extended one.

Edit: Doh!  Too slow!  :D

---

### Post by cdssf on 2007-02-24
Thanks for your response.  Can you tell me how to make it extended?  It is already primary and I do not see any way to change it.  Thanks again.

---

### Post by yabbadabbadont on 2007-02-24
Remove it and recreate it using gparted.

---

