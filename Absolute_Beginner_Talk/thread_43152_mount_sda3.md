---
title: "mount sda3"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by simple on 2005-06-20
i just intalled windows xp on a 1gb partition to test something out..format type is fat16 and i want to mount it. i don't see "sda3" in /dev/ that's what i think it's at. i know it's sda3.. how can i find it? i want to also boot it in qemu, and not really sure i need to mount it first, or anybody that has done this or can help i'd appreciate that

also, does grub only work as bootloader? would i need sda3 in that? i tried using the howto on restoring grub after installing xp after ubuntu but it didn't work.. so i just used qtparted to set the ubuntu partition as active and the fat16 not active, i tried update-grub all i think, or just update-grub and no new xp section

---

### Post by blind0wl on 2005-06-20
As far as your sda mounting problem goes, can you fdisk /dev/sda ?  Might shed some light on the setup.

---

