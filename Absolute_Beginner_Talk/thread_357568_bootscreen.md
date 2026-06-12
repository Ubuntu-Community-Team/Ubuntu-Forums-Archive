---
title: "bootscreen"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by linex on 2007-02-09
hi
i hate two questions
1) how do i edit grub settings?

2) when i boot ubuntu, i get the ubuntu boot screen with the logo and the status bar

how do i change this and replace it so insted of just logo, it shows me everything it's doing? i want it to tell me like "wireless card      OK"

thanks

---

### Post by masterpo on 2007-02-09
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo nano /boot/grub/menu.lst


remove quiet spalsh  from this line  

kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash

example

kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro


save  and exit ( ctrl + x ) and reboot .

---

### Post by linex on 2007-02-09
thanks

---

