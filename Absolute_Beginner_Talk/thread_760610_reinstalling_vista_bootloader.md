---
title: "reinstalling vista bootloader"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Nante on 2008-04-20
I have a dual boot system Vista Ultimate and Ubuntu 7.10, the service pack for vista wont install with a modified MBR and I need its bitlocker update for work, I am also having trouble with ubuntu, a patch I installed broke my wifi (badly enough that when I posted the symptoms in the wireless and networking thread it scared everyone away) so I have decided to kill two birds with one stone, remove grub, update vista, then reinstall Ubuntu. But to do that I need to know how to re install the vista bootloader, I have found a ton of how tos for xp but none for vista, any Ideas how to do it would be much appreciated.

---

### Post by LaRoza on 2008-04-20
> **Nante said:**
> I have a dual boot system Vista Ultimate and Ubuntu 7.10, the service pack for vista wont install with a modified MBR and I need its bitlocker update for work, I am also having trouble with ubuntu, a patch I installed broke my wifi (badly enough that when I posted the symptoms in the wireless and networking thread it scared everyone away) so I have decided to kill two birds with one stone, remove grub, update vista, then reinstall Ubuntu. But to do that I need to know how to re install the vista bootloader, I have found a ton of how tos for xp but none for vista, any Ideas how to do it would be much appreciated.

Get the Super Grub Disk (see the link in my sig) and restore the Windows MBR.

Boot from the disk, go to Advanced->Windows (advanced) and chose the first option I think.

(It will explain every option as you go)

---

### Post by jpyanowski on 2008-04-20
You should also use Easy BCD to use Vista's system to boot into either Vista or Ubuntu. I use it and I've had no problem. You need to install GRUB into your Ubuntut partition.

---

### Post by Nante on 2008-04-20
Thanks burning the grub disk now hopefully it will work :)

---

