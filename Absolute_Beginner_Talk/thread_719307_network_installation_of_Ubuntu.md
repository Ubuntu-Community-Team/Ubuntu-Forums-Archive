---
title: "network installation of Ubuntu"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by crazyrock on 2008-03-09
im new to linux and struggling to get it installed.
first of all what is the difference between "network installation of Ubuntu " and the one from CD.
I am trying to install linux from HD as I had problems with the CD. I used this link for refernce. I was doing the network install but kinda freaked out in the middle thinking it would install over my C drive

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I managed to get that GRUB installation working on XP. two mistakes I noticed on that link(well atleast thats how i got it working).

1) Append c:\grldr="Install Ubuntu" to c:\boot.ini. 
it should read " c:\grldr="START GRUB" "

2)kernel   (hd0,0)/boot/linux vga=normal ramdisk_size=14972root=/dev/rd/0 rw --

instead of "linux" the linux kernel should be placed ...im guessing its the one in folder "casper>>vmlinuz"
I got those from this link
[http://marc.herbert.free.fr/linux/win2linstall.html#distribution-specifics](http://marc.herbert.free.fr/linux/win2linstall.html#distribution-specifics)

Now, I did succeed in burning and booting from a CD. It comes to the ubuntu boot screen from CD but when I try to install from the CD it gives an error from boot cd. thx for ne help

---

### Post by skroops on 2008-03-09
try burning the boot cd at the slowest speed possible and attempt install again, that would be easier than a network install.

---

### Post by crazyrock on 2008-03-09
well i burned it again at 4x but no luck.i think thers something wrong wit initrd.gz file in the CD. I used the text based installer and noticed that the completion dots dont go all the way...its able to read the kernel vmlinuz fine tho. it gives this error

.......isolinux Disk Error 80, AX=4200, drive 9F

btw I still need to know wat the differnce between the network installation and Cd version is? also could someone tell me wat this initrd.gz file contains...is that wat decides wat kind of installation(network or CD) version to install?
I am asking this because i dled a copy of initrd.gz from this link 

[https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)
and pointed to taht file on GRUB's menu.lst

but thers another initrd.gz in the CD itself...I am wondering if I should point to that initrd.gz instead. BTW are there any issues wit AMD64 X2 proc. I think i recall hearin some issue wit that

---

