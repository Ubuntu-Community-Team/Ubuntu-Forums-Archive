---
title: "Dual booting in Ubunto"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Gordon Lakin on 2007-09-23
Will some kind person tell me how to dual boot a second Linux distro in addition to Ubunto? There seems to be plenty of advice for dual booting Windows but I don't use this any more.

Thanks in anticipation.

Gordon Lakin.

---

### Post by meindian523 on 2007-09-24
What you do is to install the new distro and allow grub to be written to mbr.Now Ubuntu would be not bootable,therefore,you note down the relevant portions of the Grub of the new distro and boot into Live CD.....mount your /boot and reinstall Grub on MBR,edit your new menu.lst and add the entries you wrote down earlier.Be CAREFUL About PARTITION NUMBERING!

---

### Post by Gordon Lakin on 2007-09-25
Thank you Meindian523. I am new to Ubunto and your help is most appreciated.

Regards, G.Lakin.

---

### Post by LaRoza on 2007-09-25
Ubunt**u** not Ubuntuo

Many distros will have a similar installation scheme as Ubuntu's. I plan out my partition layouts, before installing, using GParted.

---

### Post by meindian523 on 2007-09-27
> **Gordon Lakin said:**
> Thank you Meindian523. I am new to Ubunto and your help is most appreciated.

Regards, G.Lakin.

You're welcome.Post back if more help is required........:)

---

