---
title: "Macbook Pro 8,1 Can't boot from live CD."
date: 2011-06-18
forum: Apple Hardware Users
---

### Post by Brodie337 on 2011-06-18
Hi there,

I've got a Macbook Pro with rEFIt and Windows 7 installed (I'm not sure if this is relevant), and I'm running into an issue when I try to boot from the LiveCD or a USB (64 bit, due to 4GB RAM).

If I boot from the CD, the Ubuntu splash shows fine, but I run into the error message:
"(initramfs) Unable to find a medium containing a live file system"

I tried then to boot from the USB using rEFIt, but it just gets stuck at the grey screen with tux.

The disk images both are OK.

Any idea what I should try now?

If you need any more information, let me know :)

Thanks,
Brodie

---

### Post by MrSkittles on 2011-06-19
The Very same thing is hapening to me.

Mac OSX 10.6.7


15 in MacBookPro8,2
Intel i7 2.3 Quadcore 

Ubuntu-11.04-desktop-i386

Going to see if i can get a older Ubuntu to work.

---

### Post by joost1123 on 2011-06-20
Have you tried using the 64-bit Live CD?

---

### Post by CoventryMartin on 2011-06-21
I am getting the same issue with both the 32 bit and 64 bit CD images.

---

### Post by mmarsman on 2011-06-22
Same laptop, same problem.  I also have tried the 32 and 64 bit options.  

15 in MacBookPro8,2
Intel i7 2.3 Quadcore

---

### Post by CoventryMartin on 2011-06-22
It looks as if the Linux kernel can't see the CDROM drive, hence the error. I had another look today, and it appears other people are getting this problem.  I didn't check if Linux could see the hard drive. It might the SATA drivers causing a problem... I work with Linux all day (Working on Embedded Linux) and I'll be damned if I am going to mess around with it at night at home! 

I tried booting from an external CDROM drive, but that failed ever earlier!

I wonder if it means tweaks to the kernel plus a recompilation?

---

### Post by CoventryMartin on 2011-06-24
I found this:

[http://wiki.debian.org/MacBookPro#For_MacBook_Pro_13_.288.2C1.29](http://wiki.debian.org/MacBookPro#For_MacBook_Pro_13_.288.2C1.29)

It appears Debian has a *similar* issue, but they appear to get round it by mounting the image from USB as the cdrom drive!

---

### Post by CoventryMartin on 2011-06-24
I got it working! I made USB image of the CD and plugged that in, then booted from the CD-ROM. Apparently it uses the USB disc as the source of all the files. Use dd to burn .dmg file to a USB stick,

I have most of the MacBook working after updating the kernel. I don't think it can see the CD-ROM drive, and wireless does not work, even with ndiswrapper. The multi-touch pad isn't very usable.

---

### Post by supermario87 on 2011-06-25
i downloaded the lastest testing amd64 iso and made an usb stick witch dd but it cant boot

---

### Post by CoventryMartin on 2011-06-25
Did you convert the .iso file to a .dmg file?

Try the instructions on this page:

[https://help.ubuntu.com/community/Installation/FromImgFiles#Mac%20OS%20X](https://help.ubuntu.com/community/Installation/FromImgFiles#Mac%20OS%20X)

All I did was press "c" to boot from CD-ROM, and it loaded the installer fine. Make sure the USB image is also present.

IMHO, it is not worth the effort. The touchpad is not very usable (Even with the various patches and mods to the xorg.conf file) and I cannot get WiFi to work. I got bluetooth working fine by updating the kernel.

---

### Post by supermario87 on 2011-06-25
well, since i cant even boot the windows 7 dvd, i think that there is a problem with the bootloader of my mac, the dvd is working since loading dvds IN snow leopard works fine

 any help??

p.s. i've a 8,2 mbpro

---

