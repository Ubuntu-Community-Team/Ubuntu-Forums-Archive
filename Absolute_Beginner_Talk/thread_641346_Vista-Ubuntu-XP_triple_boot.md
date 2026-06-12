---
title: "Vista-Ubuntu-XP triple boot"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by lawliet89 on 2007-12-15
Hey everyone, I am new to Ubuntu and even though I've spent less than one day with it, I'm loving it so far. I have a small question before I attempt to triple boot with Windows XP.

Firstly, I had Windows Vista preinstalled with my machine and I installed Ubuntu on top of it and now I'm loving it. My question is that if I install Windows XP on another partition and then proceed to reinstall Grub, will Grub be able to recognise the newly installed Windows XP and add the appropriate item in the boot menu? Or do I have to manually add it in? If so, any ideas how I could do that?

Currently, the boot menu has three ubuntu boot items, one Vista recovery boot item added by my OEM and one more Windows Vista actual boot item.

Thanks a lot.

---

### Post by SOULRiDER on 2007-12-15
GRUB will add it automagically when you reinstall it, but ef it does not its not hard to do at all, so dont worry.

---

### Post by jpsimm on 2007-12-15
I can't help you answer that question but let me tell you what I did.

I have three hard drives in my computer.   One is SATA, one IDE and the third is USB.   I put Vista on SATA 1,  Ubuntu 7.10 on IDE and Debian on USB external Iomega.

I just wanted to see if I could do it successfully.   I think this way I have more flexibility .  I can change just one drive if I want without affecting the others and if one gets in trouble the others are somewhat isolated.   Of course I am using a desktop not a laptop.   

On boot up I get the usual screen for choices and otherwise it works fine.

---

### Post by vac on 2007-12-15
Heii.
After you did install the xp. may be it automatic detect your xp,. if it didnt you need to change menu.lst where partition of xp is ( hd0,X) change the x should.
if you still didnt manage to solve it, you may be post you menu.lst here

---

