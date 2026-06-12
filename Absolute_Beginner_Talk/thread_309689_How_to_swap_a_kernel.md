---
title: "How to swap a kernel?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by flameproof on 2006-11-30
How to swap a kernel?

Because of the wrong CPU frequence (1000MHz) with the 2.6.17-10-generic I installed successfully 2.6.17-10-386 on my AM64. Bad call!

I now just get up to some blue (X something not configured) or black screen. However, in some sort of DOS mode I can login as ROOT. 

I did a 

apt-get install linux-image-2.6.17-10-generic

But just get the Echo that I have the latest packes - but the 386 still stays.

What does the trick?

---

### Post by po0f on 2006-11-30
flameproof,

Reboot and when GRUB tells you to, hit Esc to enter the menu.  From there, just choose the -generic kernel instead of the -386 kernel.

---

### Post by flameproof on 2006-11-30
OK, but that's a one time fix and need to be done every boot.

Actually in the meantime I found a way. 

1. Boot with a working Kernel

2. In terminal I did:  gedit /boot/grub/menu.lst

..and changed the sequenz and put the old "generic" on top. 

That's actually a very good way to just test a Kernel. Don't install it, just D/L it and call it up during boot with GRUB if you need some excitement.

---

