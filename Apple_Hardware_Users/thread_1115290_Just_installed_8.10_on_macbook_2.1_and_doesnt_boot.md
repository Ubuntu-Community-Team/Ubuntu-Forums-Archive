---
title: "Just installed 8.10 on macbook 2.1 and doesnt boot"
date: 2009-04-03
forum: Apple Hardware Users
---

### Post by gandalfuy on 2009-04-03
I have installed 8.10 on a Macbook 2.1 that came with tiger.

What i did was just boot from the CD and select Install ubuntu. But now it doesnt boot at all. Im on the live CD sesion right now.

I read some stuff on the board here and i want to make sure that what i have to do is make a bootable cd with rEFIt and fix some stuff there.

Any information on this?

thanks,
aLe.-

---

### Post by WA_Garrett on 2009-04-03
Did you install rEFIt but is there no option for booting Linux?
Can you still boot into Tiger?

---

### Post by cyberdork33 on 2009-04-03
> **gandalfuy said:**
> I have installed 8.10 on a Macbook 2.1 that came with tiger.

What i did was just boot from the CD and select Install ubuntu. But now it doesnt boot at all. Im on the live CD sesion right now.

I read some stuff on the board here and i want to make sure that what i have to do is make a bootable cd with rEFIt and fix some stuff there.

Any information on this?

thanks,
aLe.-
Yes, I think you will need the rEFIt CD. are you dual booting or single-booting?

---

### Post by jamesey on 2009-04-03
do you have a MacOS partition or is the hard drive all partioned for ubuntu?

---

### Post by gandalfuy on 2009-04-03
Im 100% gnu/Linux Ubuntu now! Mac free.

I did it, im into ubuntu runing from my HD, i have the refit CD to boot. now i guess i have to install it to the HD.

How do i do that? So i don't have to use the CD. 

thanks again!
everything is working just fine! incredible, everithing works just fine almost out of the box with full sound / wireless network / extra monitor using DVI

---

### Post by cyberdork33 on 2009-04-04
> **gandalfuy said:**
> 
I did it, im into ubuntu runing from my HD, i have the refit CD to boot. now i guess i have to install it to the HD.
You should only need to use the partition tool in the refit menu to sync the partition tables, then you can boot without the CD.

You may get a long delay to boot from the normal apple logo to GRUB. If this is the case, see the FAQ for the pointer to the fix.

---

### Post by gandalfuy on 2009-04-04
where can i see some info about that delay, its taking for about 15 secs to find grub

---

### Post by cyberdork33 on 2009-04-06
> **gandalfuy said:**
> where can i see some info about that delay, its taking for about 15 secs to find grub
In the FAQ
|
|
v

---

