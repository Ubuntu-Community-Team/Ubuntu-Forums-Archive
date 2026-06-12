---
title: "startup"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by s0198hb on 2007-06-09
i have am having trouble getting ubuntu to boot. the only way i get it to boot is to have the live cd in and boot from there. if i dont have a cd in i get an error saying invaild system disk

---

### Post by ggaaron on 2007-06-09
Do you have right boot device list in bios?
If yes then do you get to grub? Because sometimes if you have multiple disc drives then they have different numbers after normal boot and after livecd boot. If it gets to grub then interrupt auto startup, click e and e again - there is (hdX,Y) <-change X to the right option (probably by testing them all from 0 to number of disks-1) press esc and then b to boot.

---

### Post by s0198hb on 2007-06-09
right does it matter that 2 of the dirves are sata and 2 drives are ide

---

### Post by ggaaron on 2007-06-09
I have one sata and one ata (named sda and hdc) - on livecd sda was hd1, but after reboot I had to change it in grub to hd0=/ So it can be your problem.

---

### Post by ggaaron on 2007-06-09
> **ggaaron said:**
> Do you have right boot device list in bios?
If yes then do you get to grub? Because sometimes if you have multiple disc drives then they have different numbers after normal boot and after livecd boot. If it gets to grub then interrupt auto startup, click e and e again - there is (hdX,Y) <-change X to the right option (probably by testing them all from 0 to number of disks-1) press esc and then b to boot.

Wow, sorry - probably you should press enter not esc for it to work.

---

