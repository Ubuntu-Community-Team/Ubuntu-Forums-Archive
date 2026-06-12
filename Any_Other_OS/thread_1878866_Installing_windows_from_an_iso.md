---
title: "Installing windows from an iso"
date: 2011-11-10
forum: Any Other OS
---

### Post by Emera on 2011-11-10
[B]I downloaded the iso from the microsoft website
It is in no way illegal or pirated.
[http://www.microsoft.com/download/en/details.aspx?id=25129](http://www.microsoft.com/download/en/details.aspx?id=25129)[/B]

I am looking to switch back to windows, and windows came on my PC when I bought it. I am not prepared to go out and actually buy a very expensive copy of windows on a disk, and have downloaded a windows XP .iso file online. I want to know how I would get that onto my USB drive so I can boot from it. Here is what I have.

Windows XP .iso
Ubuntu 10.04
BUFFALO bootable 250 GB USB drive

Can anybody give me a hand with this? Many thanks.

---

### Post by satanselbow on 2011-11-10
The file you have downloaded in an ISO (CD Image) of SP3 NOT the full installable operating system.

You would not be able to restore your system from that disc - only update a pre SP3 installation.

---

### Post by shuttleworthwannabe on 2011-11-10
Why not get Windows 7 iso they are available online download if this is the route you want to go? You can even [download an app]("http://download.cnet.com/3001-18513_4-10972600.html?spi=099f3d9072e53cca664adc71049cf5f7") to allow you into put the iso on USB, and boot off it.

---

### Post by Emera on 2011-11-11
I managed to get a windows XP iso, and I am now stuck as to how to get it onto a USB and be able to boot off it. Can anybody help me out?

---

### Post by ubupirate on 2011-11-11
> **Emera said:**
> I managed to get a windows XP iso

Was it obtained legally?

---

### Post by shuttleworthwannabe on 2011-11-11
> **Emera said:**
> I managed to get a windows XP iso, and I am now stuck as to how to get it onto a USB and be able to boot off it. Can anybody help me out?
Couple of [hits on Google here]("http://www.google.co.za/search?sourceid=chrome&ie=UTF-8&q=boot+windows+xp+off+usb+drive").

---

### Post by collisionystm on 2011-11-11
install the windows 8 preview if you want a free version of windows.

[http://msdn.microsoft.com/en-us/windows/apps/br229516](http://msdn.microsoft.com/en-us/windows/apps/br229516)

---

### Post by mips on 2011-11-12
> **Emera said:**
> I managed to get a windows XP iso, and I am now stuck as to how to get it onto a USB and be able to boot off it. Can anybody help me out?

Create a normal DOS bootable USB stick, mount the iso and simply copy everything to the stick. Boot with the USB stick and at the dos prompt run setup.exe or you can make an autoexec.bat file that automatically runs it for you.

---

### Post by shuttleworthwannabe on 2011-11-12
mips, now I am curious: how do you create a dos bootable usb stick?
/ (let me search this in the mean time)./

---

### Post by Starks on 2011-11-12
WUDT only works with Vista and 7.

Not XP.

Installing XP from USB is an immeasurable pain in the ***. You'll pull your hair out just getting it on the USB stick properly.

---

### Post by mips on 2011-11-12
> **shuttleworthwannabe said:**
> mips, now I am curious: how do you create a dos bootable usb stick?


Very easy actually.

Google & download "**128mbdos.img**", based on FreeDOS and 1MB in size.
Use dd to write the image to a USB stick *sudo dd if=128mbdos.img of=/dev/sd**x*** where x is the USB Stick.

---

### Post by BigCityCat on 2011-11-12
It would be much easier to order system recovery discs from your manufacturer for about $15 and then create your USB. Then at least you would be completely legal.

---

