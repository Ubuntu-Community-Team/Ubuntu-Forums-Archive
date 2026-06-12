---
title: "Edit Grub just for better look"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by AngelBreath on 2007-07-05
Hi toi everyone. First i have to say that i m almost completely new to the linux world. I installed ubuntu feisty and everything works fine and i m very satisfied with it. 
 My problem is that i installed it in a dual but machine with windows Vista. When i installed it the kernel was 2.6.20.15 (forgive me if i m wrong with it) After update i have 2.6.20.16 installed. Now when i boot my pc i have to choose between feisty fawn 2.6.20.15 (generic)
                                         feisty fawn 2.6.20.15
                                         feisty fawn 2.6.20.16 (generic)
                                         feisty fawn 2.6.20.16
                                         Windows Longhord

How can i edit the grub to have to choose only between feisty fawn 2.6.20.16 (generic)
and Windows Vista?

Thanks in advance

---

### Post by overdrank on 2007-07-05
> **AngelBreath said:**
> Hi toi everyone. First i have to say that i m almost completely new to the linux world. I installed ubuntu feisty and everything works fine and i m very satisfied with it. 
 My problem is that i installed it in a dual but machine with windows Vista. When i installed it the kernel was 2.6.20.15 (forgive me if i m wrong with it) After update i have 2.6.20.16 installed. Now when i boot my pc i have to choose between feisty fawn 2.6.20.15 (generic)
                                         feisty fawn 2.6.20.15
                                         feisty fawn 2.6.20.16 (generic)
                                         feisty fawn 2.6.20.16
                                         Windows Longhord

How can i edit the grub to have to choose only between feisty fawn 2.6.20.16 (generic)
and Windows Vista?

Thanks in advance

Hi and welcome I would recommend that you leave them just in case you need to boot  to maybe save your data but, this link will help you 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck

---

### Post by AngelBreath on 2007-07-05
Wow that was too fast and very helpfull. Thank you very much.

---

### Post by overdrank on 2007-07-05
> **AngelBreath said:**
> Wow that was too fast and very helpfull. Thank you very much.

;)

---

### Post by Bothered on 2007-07-05
When I update the kernel I check the new version works ok, then I comment out entries for the old version in /boot/grub/menu.lst. That way the old kernel is still installed and can be booted (by uncommenting the entries) should I later discover a problem with the later version, but doesn't appear on the boot menu.

If you decide to make changes to menu.lst,  make sure you make a back up first.

---

