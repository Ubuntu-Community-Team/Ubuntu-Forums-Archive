---
title: "Grub Menu, showing multiple ubuntu's?!?!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-05
I have a notebook dual booting ubuntu and vista, when i get to the grub menu there are a few ubuntu's...I am at work so i don't have the specific names but it goes like this:

Ubuntu....ver? - 16
Ubuntu....ver? - 16 (i think it has safe mode on the end?)
Ubuntu....ver? - 15
Ubuntu....ver? - 15 (i think it has safe mode on the end?)
ubuntu...memtest 86++

other

vista longhorn

i believe that when i updated ubuntu it added two more and increased the number by one, if i go to the /boot/grub/menu.lst and delete the older one that will just stop stop it from showing how would i go about physically removing the previous ubuntu?

thanks, Alain

---

### Post by overdrank on 2007-07-05
> **S15_88 said:**
> I have a notebook dual booting ubuntu and vista, when i get to the grub menu there are a few ubuntu's...I am at work so i don't have the specific names but it goes like this:

Ubuntu....ver? - 16
Ubuntu....ver? - 16 (i think it has safe mode on the end?)
Ubuntu....ver? - 15
Ubuntu....ver? - 15 (i think it has safe mode on the end?)
ubuntu...memtest 86++

other

vista longhorn

i believe that when i updated ubuntu it added two more and increased the number by one, if i go to the /boot/grub/menu.lst and delete the older one that will just stop stop it from showing how would i go about physically removing the previous ubuntu?

thanks, Alain

HI I would advise not deleting them because if something happens to you system then you can use them to boot and maybe save your data. But yes you can edit your grub and comment the out. ;)

---

### Post by toasterofirony on 2007-07-05
Have you installed a new kernel? 'Cause that can be where the extra entries in your grub come from. They leave the old there so you can boot into it if the new kernel misbehaves.

---

