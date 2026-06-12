---
title: "how do I get into recovery mode?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Marfish on 2007-12-08
I am installing ubuntu onto an external hard drive, and have gotten to the point where it asks me to restart. The instructions I have from another forum now say to keep the disk in the drive and boot into (sorry rescue, not recovery) rescue mode to make some changes. I booted onto the disk, and didnt have any option that said anything about rescue. Where is the option and how do I boot into that. Also, I tried booting onto my external by making my usb external the default, but it just booted from my internal, is this a problem with my bootloader being on the external hard drive? Any help would be much appreciated. I also tried booting into rescue by typing rescue into the special boot, after all the splash text and things. It booted, but then came up to a white screen and sat there. I pressed control+alt+delete and came up with an infinit loop of errors and the white screen alternating. Probably did something wrong there, huh?

---

### Post by CatKiller on 2007-12-08
When the computer starts to boot up, you'll see a message saying "Press Esc to enter GRUB menu". Press Esc to enter the GRUB menu. One of the options will be a normal boot, and one of them will be a recovery ("single user") boot that will not load a GUI but will automatically log you in as root.

---

### Post by Marfish on 2007-12-08
Thanks, but are we still talking about doing this from the disk? I cant load ubuntu on my computer at this point, usb external wont boot.

---

### Post by CatKiller on 2007-12-08
> **Marfish said:**
> Thanks, but are we still talking about doing this from the disk? 

I have no idea - I've not tried any exotic installations myself.

Have you gone into the BIOS of your motherboard to set it to boot from the external drive? Possibly with a "Boot Other Devices" option?

---

### Post by ptn107 on 2007-12-08
Try using the Live CD.

---

### Post by Marfish on 2007-12-08
Hmm, Ive tried making usb external as the default, but nothing changes. It just keeps the internal as default. I have the live cd, but I cant see an option to rescue. Theres graphics mode, but I havent seen any rescue. My bootloader is in the usb external hard drive, I would think that my computer supports booting from external seeing that its an option in the bios, but it doesnt seem to detect it.

---

### Post by Marfish on 2007-12-08
*bump*

---

### Post by Marfish on 2007-12-08
*bump*

---

