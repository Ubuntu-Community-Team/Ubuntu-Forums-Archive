---
title: "Asus M5A99X EVO chipset and driver support?"
date: 2013-05-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Velorium117 on 2013-05-22
I recently installed Ubuntu on my system and I can't figure out how to get the drivers to work on Linux. The install disk that comes with the mobo includes a "isolinux" folder containing an "isolinux.bin" and some other jargon. The disk also has a folder called "Linux drivers" containing a text document that simply reads "ensure to update to the latest Linux kernal". I'm just looking to see if anyone has an idea how to obtain the proper drivers, or make the existing install disk work?I'm pretty green when it comes to Linux systems so bear with me if I sound "noobish". 

TL;DR I need Linux version drivers for my Asus M5A99x Evo motherboard.

---

### Post by gordintoronto on 2013-05-22
Drivers work very differently in Linux than what you are used to. Most drivers are included with the kernel, so it "just works." If you have installed Linux and it runs, you have no need to chase after drivers.

Since your motherboard is very new, older versions might not work as well as 13.04. Even with 13.04, it's possible some bits won't work, such as the Ethernet port. 

Wireless adapters are a special case, some just work, some work if you say the appropriate "shazaam," some work after quite a struggle, and some never work. Webcams and printers are similar.

My entire system "just works," including all of the above, and a scanner.

Video cards usually just work, but then you can get better performance by installing an "additional driver," which is done via the Ubuntu Software Centre.

Good luck, let us know how it works out.

---

### Post by Velorium117 on 2013-05-22
Thanks for the info. I guess I'm in the unfortunate case of things no "just working" lol. The main issue is my ethernet adapter not working, so I can't get online to download other bits from Ubuntu to fix my graphics drivers and so on.

---

### Post by gordintoronto on 2013-05-23
You can open Terminal and enter this command: lspci

It will produce 15 to 20 lines of output, and one of them (near the bottom) will look like this:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

On my system, the important data is "RTL8111/8168B" and "rev 02". I would plug that into Google with the words "linux" and "solved".

Are you using Ubuntu 13.04? If it doesn't work there, it is possible that it will take months for your Ethernet port to be supported. Is there any chance you could use a wireless adapter, or plug in an add-on card with an older Ethernet adapter?

---

