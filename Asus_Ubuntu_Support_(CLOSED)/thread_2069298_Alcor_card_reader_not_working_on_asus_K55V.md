---
title: "Alcor card reader not working on asus K55V"
date: 2012-10-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Mickser_52 on 2012-10-10
I recently got an Asus K55V laptop. I eventually got dual-boot and right click to work. There is one problem which I cannot find a solution to.

The built in sd card reader will not work. It works perfectly in Windows 7 but not in ubuntu 12.04. 

lsusb command shows: Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp.but when I put in a SD card nothing happens.

Photography is a hobby of mine and I had no problem with my last laptop with 11.04 and Rapid photo downloader, downloading from an sd card.

I can download in Windows and then view and edit from Ubuntu but that involves restarting and wastes time. 

Has anyone any solution to this problem.

p.s If I try to connect my Canon dslr directly by USB in Ubuntu I get an error message and it will not mount.

---

### Post by Mickser_52 on 2012-10-22
It appears the card reader is a Realtek Card reader not Alcor. It is now working after I found this link [http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb]("http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb"). I saved it and installed it with Ubuntu software center. 

Still no luck on connecting Canon dslr directly to the laptop but I can now download without having to switch to Windows 7 first.

---

### Post by lucamedici on 2012-10-30
Hi! I've the same notebook, asus k55v and i've a problem whit the webcam... the picture is very dark and whit a bad resolution, don't you think?

---

### Post by rait07 on 2012-10-31
i have Asus k55v laptop but its have little problem with screen..how to i solve it...

---

### Post by lucamedici on 2012-11-01
screen? What kind of problem?

---

### Post by Rickytrix on 2012-11-10
will this also work on ASUS X401a?, same problem, sd slot work on win 7 ,not on Ubuntu, i got rid off WIN, so full ubuntu boot.

---

