---
title: "Grub giving me the option of logging into k7 and 386 Ubuntus?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by sweeper on 2006-06-05
I had the 686 kernel and changed to the k7 kernel now I have the option of logging into 2 different Ubuntus and one of them is 386? Totally confused.

---

### Post by rado_london on 2006-06-05
maybe you didnt remove the default kernel. Check if it installed in synaptic. Then remove it if you dont need it anymore.

---

### Post by sweeper on 2006-06-05
Thanks, there is Linux 386 and Linux-image 386, I take it I uninstall both?

---

### Post by Klaidas on 2006-06-05
If you update/install a kernel, it appear in your GRUB menu.
If your new kernel work fine, you can remove the old kernel, or you can just remove the BRUB entry (see [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto) )
If the new kernel doesn't work, then, wel... That's why GRUB didn't delete the old kernel from the menu - you can boot up in the old one :)

---

### Post by sweeper on 2006-06-05
Ah I see, thanks guys
:)

---

