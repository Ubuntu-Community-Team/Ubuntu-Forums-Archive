---
title: "Could someone tell me how to alter grub please."
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by NorfolkPud on 2007-05-04
Hi
I have XP and Uubunto installed independently on separate drives but I have to enter the Bios to select which os should boot. Is there any way to edit grub so that it gives me a choice of os's.
Ubuntu is on drive1 and XP drive 0. I would be grateful if someone could tell me how to do this in Terminal.
Thanks

---

### Post by Kobalt on 2007-05-04
You need to change the drive on which Grub is installed and then add to your /boot/grub/menu.lst file a line for Windows. Here is a guide : [https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29#head-62dd4ea50c42fb3113752a272d7100469d733668](https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29#head-62dd4ea50c42fb3113752a272d7100469d733668)

---

### Post by NorfolkPud on 2007-05-04
Thanks Kobalt
I will try that

NorfolkPud

---

