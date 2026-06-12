---
title: "Partitioning Ubuntu issues"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by s7alk3r91 on 2008-01-18
im trying to Duel Boot install Ubuntu on my 150gb Raptor hd (XP already installed) and im trying to partition it so it only takes up like 15% of my hd space but the minimum its letting me go down to is 67& and my hard drive is already like 52% full so what do i do here lol yah im a noob

---

### Post by h84ll1 on 2008-01-18
> **s7alk3r91 said:**
> im trying to Duel Boot install Ubuntu on my 150gb Raptor hd (XP already installed) and im trying to partition it so it only takes up like 15% of my hd space but the minimum its letting me go down to is 67& and my hard drive is already like 52% full so what do i do here lol yah im a noob

hiya! welcome! i'm new too but i've managed to get ubuntu dual booting.
well, firstly, if it's already that full it will never come down to 15%.  If you mean you only want ubuntu to take up 15% then fair enough, just that confused me a little. lol. :confused:

anyhow, do you have the drive partitioned already with the xp on a partition? sounds like maybe not. in which case you may need to get some software to partition your drive in windows first, just to gather up all the windows stuff in one separate place.
Gparted is a free program you could use to do that. not sure of others but maybe have a google on it.

anyone else know what we could do!!?

---

### Post by thelatinist on 2008-01-18
> **s7alk3r91 said:**
> im trying to Duel Boot install Ubuntu on my 150gb Raptor hd (XP already installed) and im trying to partition it so it only takes up like 15% of my hd space but the minimum its letting me go down to is 67& and my hard drive is already like 52% full so what do i do here lol yah im a noob

You are trying to resize your Windows partition, right?  If that's 52% full, there's no way to get it to 15%.

If you are trying to make your Windows partition 85% and your Ubuntu partition 15%, then just resize your Windows partition to 85%, leave the 15% empty, and install Ubuntu chosing the option to use the largest free space.

---

### Post by s7alk3r91 on 2008-01-18
i think i figured it out so the 67% of my hard drive is like windows on top of what im guna use for Ubuntu? so if im using 52% of my hard drive and wanted Ubuntu to be 15% i would want it to take 67 then lol funny how that worked out

---

### Post by thelatinist on 2008-01-18
> **s7alk3r91 said:**
> i think i figured it out so the 67% of my hard drive is like windows on top of what im guna use for Ubuntu? so if im using 52% of my hard drive and wanted Ubuntu to be 15% i would want it to take 67 then lol funny how that worked out

No...67% is how big you would be making your Windows partition. You want it 85%.

---

### Post by s7alk3r91 on 2008-01-18
alright so that bar in the Ubuntu install partition thing u change creates ur windows partitions size

---

