---
title: "/boot is 97% full"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by NobodySpecial on 2006-05-20
I booted up today and received a message that the boot partition is 97% full.  I was suprised as I gave the partition 100 MB space.  I do have the original 386 kernel as well as the K7 kernel which is working well.

Questions:
1. Should I apt-get uninstall the 386 kernel which I'm no longer using?
2. Do I need to edit the /boot/grub/menu.lst file?
3. Do I need to physically delete anything from /boot?

Thanks for helping!

---

### Post by Kimm on 2006-05-20
you can just as well remove the 386 kernel if your k7 kernel is working properly. And no, you should need to manualy remove anything or edit the grub menu

---

### Post by Sef on 2006-05-20
In Synaptic, you can delete local or outdated software.

System > Administration > Synaptic Package Manager > Status

---

