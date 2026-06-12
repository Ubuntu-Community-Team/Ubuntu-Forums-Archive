---
title: "Ubuntu and windows"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by mikeee6562 on 2007-11-26
I am new to Ubuntu. I want to try it, but I want windows to boot first. how do I do this.
Thanks

---

### Post by skyjacker on 2007-11-26
> **mikeee6562 said:**
> I am new to Ubuntu. I want to try it, but I want windows to boot first. how do I do this.
Thanks You can try it without making any changes to your system by using the "live cd".

---

### Post by overdrank on 2007-11-26
> **mikeee6562 said:**
> I am new to Ubuntu. I want to try it, but I want windows to boot first. how do I do this.
Thanks
HI and welcome, as address in your other thread please do not make multiple threads on the same subject. You can make vista the option to boot first by editing the grub and here is a good link to instruction.
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

Edit of course you can modify the grub after Installation of Ubuntu

---

### Post by jken146 on 2007-11-26
You will have the option to boot either OS.  You can change their order in the bootloader (GRUB) menu.  For a guide to installing Ubuntu alongside Windows, see here: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by mummra1 on 2007-11-26
If you decide to install Ubuntu on your PC, be sure not to overwrite your windows partition.:oops:  Ubuntu is capable of dual-booting, and after you install it, you can choose whether you want to boot into Windows or Ubuntu.

---

### Post by LowSky on 2007-11-26
in /boot/grub/menu.lst, change or add this line

```
 default n 
```
where n is a number position of your windows entry, starting from 0. [/code]

---

### Post by Nikitas350 on 2007-11-26
It's very easy just install ubuntu and i will tell you how to do it...

---

