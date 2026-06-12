---
title: "[SOLVED] freeze during loading screen"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by stainless_steel on 2008-03-07
my ubuntu 7.10 is great, but 1/10 or 1/5 times it boots it freezes during the loading screen. the orange bar is in the third little section. (always the same place)

im using a typical emachines computer with amd sempron processor, loads of ram, s3 unichrome video card, the usual.

---

### Post by uberlube on 2008-03-07
this happened to me when i first started with ubuntu. Try adding 'irqpoll' to the boot process by pressing F6 during the liveCD grub. Also try adding 'vga=791' if you still cant get into the desktop.

---

### Post by stainless_steel on 2008-03-10
where exactly do i put it? and this is while booting with the cd?

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper /initrd.gz quiet splash --

---

### Post by stainless_steel on 2008-03-16
well, it hasnt happened in awhile (i changed v-cards) so...

---

