---
title: "[SOLVED] Installing Suse 10.3"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-02-20
I want to play around with SUSE 10.3. I plan to install it onto my Gutsy drive. Am I going to be in for a suprise like not being able to boot Gutsy after this move??

---

### Post by Origin415 on 2008-02-20
After you install it you may have to reconfigure grub before you can back to ubuntu, but thats about it.

---

### Post by kindafunnylookin on 2008-02-20
> **Origin415 said:**
> After you install it you may have to reconfigure grub before you can back to ubuntu, but thats about it.

Thanks, guess I can use SUPER GRUB DISK for that.

---

### Post by bodhi.zazen on 2008-02-20
The suse installer should recognize and set up grub for you no problem. I doubt you will need to do anything manually.

You will need to either user chainloader to boot ubuntu or manually update (suse) /boot/grub/menu.lst every time you update the Ubuntu kernel.

---

### Post by kindafunnylookin on 2008-02-20
> **bodhi.zazen said:**
> The suse installer should recognize and set up grub for you no problem. I doubt you will need to do anything manually.

You will need to either user chainloader to boot ubuntu or manually update (suse) /boot/grub/menu.lst every time you update the Ubuntu kernel.
Thank you for that warning. It will save me a lot of time after the next update.

---

