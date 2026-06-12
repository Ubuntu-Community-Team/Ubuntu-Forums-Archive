---
title: "Installing Ubuntu On an already dual boot system."
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-01-21
I am going to install Ubuntu 6.10 Edgy on a system which already has a dual boot (LILO) installed by Mandriva Powerpack 2007, the dual boot being for Windows and Mandriva. If I install Ubuntu now, will it try to accept the already installed bootloader by Mandriva or will it clash with it. Or rather, how should I go about it as I also have /home, /,/boot and /swap partitions already from Mandriva. Thanks.

---

### Post by Bachstelze on 2007-01-21
I assume you want to keep Mandriva. Then just install Ubuntu on a spare partition. You can share /boot and swap but not /home. Just let Ubuntu install GRUB, we'll configure it to boot also Mandriva later.

---

### Post by keith11 on 2007-01-21
I am sorry I gave out the impression I want to keep Mandriva. I actually want to remove Mandriva and just have Ubuntu and Windows on my system. Thanks.

---

### Post by Bachstelze on 2007-01-21
Then just install UBuntu over it, you can use the same partitions but be sure to format them before.

---

### Post by keith11 on 2007-01-21
Thank you so much for the help and prompt responses. :)

---

