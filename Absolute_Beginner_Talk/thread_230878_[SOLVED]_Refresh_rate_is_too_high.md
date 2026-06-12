---
title: "[SOLVED] Refresh rate is too high"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by SPW06 on 2006-08-06
Hi,

I'm trying to install an lampp server. When I installed it, I had to use the F4  menu and swith it from VGA to 1024x768x16 to get it to work. However, when I boot hrom my HD, my monitor warns my that the refresh rate is too high. The only way I can get this to work is to boot into recovery mode. How do I fix this?

PS: This computer is older

---

### Post by John.Michael.Kane on 2006-08-06
I would say that you may have to manualy edit xorg to add the propper res rate. also what is the complete system spec's?

---

### Post by lamego on 2006-08-06
If you are refering to the grub text mode refresh rate I got the same problem.
You will need to use another resolution by editing /boot/grub/menu.lst .
On the kernel lines add the option vga=number .
Use a mode number from this [table]("http://www.8ung.at/spblinux/grub.htm")  .

---

### Post by SPW06 on 2006-08-06
Thank You!

---

