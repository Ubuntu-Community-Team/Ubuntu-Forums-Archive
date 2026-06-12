---
title: "Grub bootloader for Breezy question ?"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by jmejedi on 2005-11-09
Why does Ubuntu Breezy's Grub bootloader have some many entiries; that is, the many different OS options ???

Thank you for your time,

JME

---

### Post by canadianwriterman on 2005-11-09
[QUOTE=jmejedi]Why does Ubuntu Breezy's Grub bootloader have some many entiries; that is, the many different OS options ???

Thank you for your time,

JME[/QUOTE]

Are you talking about the entries in the menu.lst file or the choices you get on your screen when you boot up your computer?

---

### Post by jmejedi on 2005-11-09
the choices you get on your screen when you boot up your computer.......

Thanks for quite reply, take care,

JME

---

### Post by earobinson on 2005-11-09
there is 3 entrys for every kernel installed on your computer. (OS, rescue, Memtest)

edit: fixed based off kapres post

---

### Post by Kapre on 2005-11-09
[QUOTE=jmejedi]Why does Ubuntu Breezy's Grub bootloader have some many entiries; that is, the many different OS options ???

Thank you for your time,

JME[/QUOTE]

jmejedi - If your dual booting with another OS, you'll really have many entries on your GRUB list. Ubuntu comes with 3 (OS, rescue, Memtest). If this is what your askign for, it is by default.

K

---

### Post by jmejedi on 2005-11-09
Thanks guys for info. I was just curious as to why Ubuntu did this; other Linux OSs I have tried don't do this, seems much simiplier.

---

### Post by earobinson on 2005-11-09
I assume the dev team thought it was important to have a rescue, Memtest setup.

also the default install of ubuntu hides all this from the user on bood (you have to press esc to see it)

and every linux distro i have used keeps the option to boot to the old kernel unless you remove it. that way if the latest kernel is buged for you, then you can simply boot to an older one :)

---

### Post by eric0919 on 2005-11-09
I have been messing with my kernel and have a bunch of extra lines.  How can i get back to just the original and my windows partition?

thanks Eric

---

### Post by earobinson on 2005-11-10
edit /boot/grub/menu.lst

---

