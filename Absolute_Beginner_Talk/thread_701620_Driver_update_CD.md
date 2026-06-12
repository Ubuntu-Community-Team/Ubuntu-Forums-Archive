---
title: "Driver update CD ?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by GonerNL on 2008-02-19
hi,

I'm going to install Ubuntu 7.10 on a PC that already dual-boots into Mandriva 2008 and Windows XP Pro - using NTLDR.

- First of all, what is the option 'install with driver update cd' exactly ? how is it different from a normal start/install ?

- can I put Grub on the Ubuntu partition during installation and how do I then re-boot into Ubuntu after installation to create a bootsector (with 'dd if= ... of=...')  to use in boot.ini ?? 
With Mandriva there's a rescue option on the DVD to get into Linux if something goes wrong ...

thanks in advance,
Rob

---

### Post by jken146 on 2008-02-19
> **GonerNL said:**
> - First of all, what is the option 'install with driver update cd' exactly ? how is it different from a normal start/install ?
I don't know exactly.  I've never used it and I don't think most people need to.

> - can I put Grub on the Ubuntu partition during installation and how do I then re-boot into Ubuntu after installation to create a bootsector (with 'dd if= ... of=...')  to use in boot.ini ?? 
With Mandriva there's a rescue option on the DVD to get into Linux if something goes wrong ...
If I were you, I'd let Ubuntu put GRUB on the  MBR.  It does a good job of detecting other distros and adding them to /boot/grub/menu.lst.

---

