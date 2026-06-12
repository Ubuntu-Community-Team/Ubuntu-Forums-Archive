---
title: "LOST GRUB, please help."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by backflip on 2008-03-31
I use 7.10 and over the weekend I decided to dual boot with Mint 4. I was getting lots of problems with mint, so I deleted the Mint partitions and now I can't boot into Ubuntu. I get error 15 or when I tried super grub disk I got 'file not found.'
I'm using a livecd now and can see my ubuntu installation (as I can when I checked with gparted livecd). I don't know how to fix grub though so that I can boot into it.
Any help would be much appreciated. Please assume that I've no knowledge so I would need a step-by-step guide.
Thanks.

---

### Post by kane77 on 2008-03-31
I would bet something that this is because i had info about mint kernel in it but cannot find it anymore.. so first of all remove all refernces to mint kernels from /boot/grub/menu.lst
you should do sudo gedit /boot/grub/menu.lst

if that doesn't solve your problem try the grub recovery which you can find here: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Duck2006 on 2008-03-31
Or you can try this one to restore grub.

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by backflip on 2008-03-31
Thanks, I've tried some the suggestions and the problem seems to be that something called stage 1 in grub/boot is missing. How can I rectify that?
Thanks.

---

