---
title: "second linux distribution on P-ata drive"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by david2007 on 2007-09-03
hello and goodmorning to everyone !
I am a new ubuntu user , aktually i have it on my maschine two days and i find it quite attraktive . Everything work ok from the first day allthough i had some problems with my screen resolution which is 1680x1050 (problem solved).
I have two sata drives and one pata . On the one i have my windows , on the second ubuntu and i wanted to install Mandriva 2007 on the pata . 
But the Mandriva doesnt boot . I tried to add manuallyto  the  boot file in the UBUNTU  but it has a problem booting up from the PATA drive .I put the right location- i am pretty sure because i checked the menu.lst file on the Mandriva OS and i copied the location ;-)
This is also the reason why i installed the Ubuntu on my second sata drive , i first tried on the PATA but i couldnt boot it from there . Probably its a hardware issue and it doesnt want to boot from my 40gb pata. 
Also i tried to change the priority of booting and put the pata first , also didnt work. :confused:
My second choice is to partition the sata drive where ubuntu is and install there my second linux distr. 
(Probably i will install sabayon instead of Mandriva but this is irrelevant , just experimenting arround):popcorn:.
For any help i will be grateful , thanx !

---

### Post by hyper_ch on 2007-09-03
Plz post your /boot/grub/menu.lst

---

### Post by david2007 on 2007-09-03
around 5 i am going home and i will post the menu.lst file ;)

---

### Post by david2007 on 2007-09-03
so this my menu.lst with the option to but also mandriva linux, the first three options ..

title linux
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hdb1  resume=/dev/hdb5 splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

title linux-nonfb
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hdb1  resume=/dev/hdb5
initrd (hd0,0)/boot/initrd.img

title failsafe
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hdb1  failsafe
initrd (hd0,0)/boot/initrd.img

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=07c55680-31d5-46a8-bb67-893a90e6662e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=07c55680-31d5-46a8-bb67-893a90e6662e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=07c55680-31d5-46a8-bb67-893a90e6662e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=07c55680-31d5-46a8-bb67-893a90e6662e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

