---
title: "tri booting suse, ubuntu, and XP"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-09-30
okay right now I have windows XP, vista, and ubuntu on my computer. The first partition is XP, second is vista, 3rd is my linux swap, and fourth is Ubuntu. What I'd like to do is put Suse (10.1 if it matters at all) on the vista partition. What are the odds of this making Ubuntu or Windows non bootable.

---

### Post by Qrk on 2006-10-01
SuSE will detect Ubuntu and usually will add it into GRUB. It will  do the same with Windows XP (just like Ubuntu did) 

The only problem is that SuSE's grub won't detect Ubuntu's kernel updates and visa versa. Its not hard to fix, just edit Grub manually, which is easy because you only need to follow the template.

---

### Post by mongooseman1128 on 2006-10-01
so whenever I do a kernel update for Ubuntu I just need to add the new kernel to Grub? (I'm pretty new to linux so would you mind telling me where to find Grub)

---

### Post by think13 on 2006-10-01
You simply edit /boot/grub/menu.lst

sudo gedit /boot/grub/menu.lst

find where the lists of operating systems are and add the new Ubuntu kernel. (not sure of the specifics on doing that)

---

### Post by mongooseman1128 on 2006-10-01
awesome, thanks.

---

