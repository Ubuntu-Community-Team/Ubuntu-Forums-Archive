---
title: "Can I use acronis OS selector?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Rioku on 2008-03-06
Was wondering if i can use acronis OS selector to triple boot ubuntu as I already have 2 OS's installed on my laptop with acronis OS selector.

My main worry is that the grub loader will ruin my laptop.. how can i make sure or select the grub loader to install on the partition I want ubuntu on?

I would like it so i have
Xp media centre (currently using)
Vista (currently using)
Ubuntu (want to be in the OS selection list)

---

### Post by Rioku on 2008-03-06
*bump* sorry just realy need this answered before i try it out myself and end up breaking something

---

### Post by justin whitaker on 2008-03-06
Yes. You just have to make sure that you tell Ubuntu not to write to your MBR, because Acronis will be there. 

You then need to edit Acronis so that it can boot to XP and Ubuntu. I assume that this is something like using GAG or BootMagic, so it should be easy to do.

---

