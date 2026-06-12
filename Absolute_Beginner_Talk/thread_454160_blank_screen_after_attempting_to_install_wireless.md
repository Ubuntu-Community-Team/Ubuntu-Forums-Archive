---
title: "blank screen after attempting to install wireless"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Feed on 2007-05-25
ok...so i get the dual boot going on my HP Pavilion Notebook with an AMD Turion 64 x2. upon powering up, i got the proper dual boot menu to select my OS. i could boot into Ubuntu or Windows Vista.

i googled a tutorial to get my wireless Broadcom thing set up and followed all the procedures.

btw, i installed ubuntu studio.....so im guessing its 7.04, fiesty.

after completeing the tutorial on the ndiawrapper, i had to reboot and i get the ubuntu splash screen, but after that it goes into a blank screen. the first time i got back into vista and found some way to enter recovery mode and get to my login screen and can eventually get into the desktop of ubuntu. but nothing worked at all....i kept getting permission errors and junk. couldnt do anything....

so i reinstalled and followed the same procedure only to get the blank screen again....

is ubuntu gonna be too difficult for me? i really want to learn this OS so any info would be helpful

---

### Post by shamreez on 2007-05-25
Hi,

The two links below should guide you to most of the issues present in Ubuntu for HP botebook users.
All the best...and dont give up it is a lovely system once you finish the installation...

For Generic DV6000 series

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29#head-dd3315017e3efc368510f9b2b7022f8aeb15451e")

Ndis wrapper installation (In case you doubt your wireless installation was wrong

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by jargoman on 2007-05-29
Your card might not have a broadcom wireless card. Loading the wrong driver might have adverse affects

try using 
$ lspci

This will give you a list of pci devices on your computer. Your wireless card should be in there.

If this command
$ lspci | grep Broadcom

gives this result:
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Then use my tutorial I put up a few hours ago. You can copy and paste the commands and I've included the drivers.

[http://freeshells.ch/~jargoman/ndiswrapper.html](http://freeshells.ch/~jargoman/ndiswrapper.html)

please let me know if it works by leaving a post. I'd like feed back.

---

