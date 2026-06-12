---
title: "did 7.04 install?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Techboy_Miata on 2007-06-11
that is my question.
well one of them anyway, it seemed like an appropriate subject. heres the lowdown.
i have 2 physical drives  my new 160 Gig SATA which windows has all to itself and my old but still working (at least 3 years and still going) 80 Gig Maxtor IDE which i wish Ubuntu to have.
for the record and relevance i have XP home installed to the SATA. i tried installing Ubuntu on the IDE, everything seemed to go fine there were no indications of problems during the install however when i rebooted there was no new boot loader or anything. it went straight to windows as if i had not done anything at all. what happened? is this the result of this particular ver or is my SATA causing problems again? (it cost me over $100 to find out why windows wouldn't install to the SATA originally.) 
on a final note i chose the guided install use the whole drive at the partition section.

i love what i see so far in the latest 7.04 live ver however if i cannot get it to install properly i would at least like to know why and whats responsible so maybe i can fix it. 
much thanks:)

Josh

---

### Post by Cypher on 2007-06-11
I think there is some issue with having a SATA and IDE drive in the same system. For some reason I think GRUB always gets installed to the wrong drive (in this case IDE) and since the SATA is probably your boot-drive, nothing shows up.

However, if you were to use the Live CD to get back into Ubuntu and check out the IDE drive you might finds all the partitions are there.

---

