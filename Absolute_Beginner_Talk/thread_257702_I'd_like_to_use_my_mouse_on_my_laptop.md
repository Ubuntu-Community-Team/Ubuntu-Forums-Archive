---
title: "I'd like to use my mouse on my laptop"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2006-09-14
I have a compaq presario 1200 Pentium III
Xubuntu (Dapper) installed yesterday (Love it, it runs fast on my old machine)

I would like to use a mouse though instead of the touch pad, though plugging in the mouse doesn't do anything. How do I set my mouse up?

Thanks,

Maarten.

---

### Post by neoeden on 2006-09-14
What kind of mouse is it? Is it usb (rectangle connector) or ps2 (circle)? If it is usb, it usually works once you plug it in. If no, try rebooting with it in and see if that works. 

If not, we get try editing your /etc/X11/xorg.conf file.

---

### Post by stroopwafel on 2006-09-14
I have a ps/2 mouse with a scroll button (elitech, that works fine on other computers)

I've rebooted the laptop, but only my touch pad works. My mouse doesn't respond AT ALL.

---

### Post by stroopwafel on 2007-01-04
I still can't use my mouse on my laptop PC. (compaq presario 1200 12xl325 PIII 600 MHz, XUBUNTU)

How do I change the settings on my computer to make the mouse work?

---

### Post by scrooge_74 on 2007-01-04
you are going to have to check xorg.conf in  /etc/X11

my ps2 mouse sometimes wont work and I have to shutdown and then boot up again

---

### Post by encompass on 2007-01-04
Also be sure to do a cold restart.  PS2 is not hot plug able.  So make sure you so that.  You should also make sure your bios doesn't shut off the ps2.  MAny laptop bioses do it.

---

### Post by fredster001 on 2007-01-04
get a convertor from the circular one to usb if nothing else works. That should do it....

---

### Post by stroopwafel on 2007-01-04
> **encompass said:**
> Also be sure to do a cold restart.  PS2 is not hot plug able.  So make sure you so that.  You should also make sure your bios doesn't shut off the ps2.  MAny laptop bioses do it.

I can't seem to get in to the BIOS of my laptop. at start up i just keep pressing <del> or f2 f3 or f12, but nothing seems to work.

any suggestions?

---

### Post by scrooge_74 on 2007-01-04
try ESC or even F1

There is a thread somewhere with detail for entering bios for different brand names if I can find it i will let you know

---

### Post by stroopwafel on 2007-01-04
> **fredster001 said:**
> get a convertor from the circular one to usb if nothing else works. That should do it....

Since I have to buy an adapter I thought I might as well go for a keyboard AND mouse ps/2 to USB adapter. (see link: [http://www.1powershop.com/products/computer-networking/usb-to-dual-ps2-adapter-converter-cable.html](http://www.1powershop.com/products/computer-networking/usb-to-dual-ps2-adapter-converter-cable.html))

Will this work with (X)Ubuntu?

---

### Post by jpeddicord on 2007-01-04
Run```
sudo dpkg-reconfigure xserver-xorg
```with the mouse plugged in. It should ask you about setting up your mouse.

---

### Post by encompass on 2007-01-04
Yes it should...
But um... are you sure you can't get into the bios...
Try escape... it you whatch your computer as it boots... it will tell you what to press.  If it doesn't it is probably escape. If you missed it and it is doing the grub count down... it is ok to press cntrl alt delete to restart, and try again.

---

