---
title: "A few questions about Ubuntu."
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by socialistic on 2008-04-21
I'm debating on getting ubuntu to dual boot with my tweaked win xp pro sp2.

A few possible compatibility issues/questions come to mind.

1.  I use bluetooth software on my desktop and laptop.  It lets me connect my pc and phone together via bluetooth wireless.  With this software, I am able to "dial up" through my phone to my cellular service provider's data network...the internet.  Can I do this with ubuntu?  If not...is there bluetooth software for ubuntu that I could use to get online through my phone like I do with win xp?

2. My laptop is only used for 2 things...portable internet, and tuning my car.  The tuning software is windows based...is it possible to run windows based programs with ubuntu?

3.  Are hardware compatibility issues a common problem?  I'm not running anything spectacular...but still curious as to how this will work.

4.  When installing Ubuntu, will it install itself on a new partition if I'm wanting to keep Windows...or will I have to use something like Partition Magic to create a new partition, and tell ubuntu to install there?  Also...will I have to add a boot command to the system startup login order to dual boot, or will ubuntu do all of this for me without any hassle?

My custom-built desktop:

Intel Pentium D 945 Dual-Core 3.4GHz(Overclocked to 3.8GHz)
ASROCK DUAL-VSTA Motherboard+on-board audio+usb 2.0+IEEE 1394
1GB DDRII
Sapphire ATI Radeon x1300 PCI-E 512MB DDRII
Dual Western Digital 320GB IDE hard drives
Windows XP Pro SP2(heavily tweaked)
Multi-Format Double Layer DVD/RW+CD/RW Drive
CD/DVD ROM
Floppy
10/100 Ethernet
Bluetooth Enabled

My laptop;

Gateway MX7118
Mobile AMD Athlon 64 3400+(2.2GHz)
512MB DDR
ATI Radeon Xpress 200M 64MB Shared
80GB HDD
Multi-Format Double Layer DVD/RW+CD/RW Drive
6-in-1 Memory Card Reader
Integrated 802.11g Wireless
Integrated 10/100 Ethernet
Integrated 56k Dial-Up
Bluetooth Enabled

Thanks in advance! :)

---

### Post by unclejac on 2008-04-21
Hi you might want to check out a few of these guides.: 

[Complete Guide to Installation in Ubuntu]("http://ubuntuforums.org/showthread.php?t=500020")

Generally you can spot hardware issues by using Ubuntu's live CD. This enables you to try it before making any changes and installing it onto your machine. Get your live CD here:

[http://www.ubuntu.com/getubuntu]("http://www.ubuntu.com/getubuntu")

A dual boot setup is handy to have initially, it can help your transition from windows. But trust me once you learn the basics in Ubuntu, you'll not want to got back hehehe :-D Just do a search on the forums here and you will find a guide. Thats what i ended up doing with my Vista setup, all be it I havn't been into Vista in months ;-)

There is also a program called Wine, which allows you to run windows apps in Linux. have a look here:

[URL="https://help.ubuntu.com/community/Wine"]
https://help.ubuntu.com/community/Wine
[/URL]

hope some of this helps

---

### Post by ad_267 on 2008-04-21
I don't know about the bluetooth, I haven't used that sorry.
Some windows programs can work with Ubuntu using software called wine. See if your software is listed here for some idea of how it will work with wine: [http://appdb.winehq.org/](http://appdb.winehq.org/)
Your hardware shouldn't be a problem.
The ubuntu liveCD comes with gparted which can be used to resize and create partitions, or you can get the installer to shrink your windows partition for you.
Ubuntu will install it's own boot manager called GRUB onto your master boot record in the windows partition, it can be removed later if you want to remove Ubuntu.

---

### Post by socialistic on 2008-04-21
Awesome, I'll check out those links tomorrow when I get the chance.

It seems like most of my questions have been answered, or will be answered with the guides...apart from the bluetooth.

I guess I could just try it, and use wine...and hope the bluetooth enables and dials properly.

Getting ubuntu will take some time as my internet speed is based on my phone's reception(up to an average of 768kbps with speed bursts of up to 2.4mbps)...and here at home I average about 130kbps, max of 16-17kbps when downloading...due to bad reception in this area. :(

---

### Post by ad_267 on 2008-04-21
I found this for bluetooth: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
From that page there is a link to a list of bluetooth devices with Linux support: [http://www.holtmann.org/linux/bluetooth/features.html](http://www.holtmann.org/linux/bluetooth/features.html)
Even if your device isn't listed there it may still work.
This might also be useful: [http://tuxmobil.org/phones_linux.html](http://tuxmobil.org/phones_linux.html)

Good luck, hopefully everything goes smoothly. If you have any problems and can't find an answer by searching there are heaps of helpful people on the forums.

---

