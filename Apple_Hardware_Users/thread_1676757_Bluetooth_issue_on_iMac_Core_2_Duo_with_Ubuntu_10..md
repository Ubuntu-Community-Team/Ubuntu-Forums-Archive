---
title: "Bluetooth issue on iMac Core 2 Duo with Ubuntu 10.4"
date: 2011-01-27
forum: Apple Hardware Users
---

### Post by Jevmann on 2011-01-27
Hi all,

I've got Ubuntu 10.4 on dual boot on an iMac 10,1 Core 2 Duo and after I ran the first update my apple bluetooth keyboard can no longer connect to Ubuntu, and neither can the bluetooth mouse. 

Luckily I had a spare usb mouse floating around, so I checked the bluetooth settings. Ubuntu does see both my keyboard and my mouse but only makes a connection for a couple of moments and then breaks it.

Also, when I try to use the mouse, I am asked for a PIN. Is this the product id?

Anyone else had this problem and know how to fix it? Am I missing a bluetooth driver?

Any help is greatly appreciated.

---

### Post by ZeroLinux on 2011-01-28
There is a solution for 10.04, but it is a bit complicated
It is better to upgrade or to reinstall to 10.10. It contains new BT driver.

---

### Post by Jevmann on 2011-02-04
Thanks for the reply, although I have now got it working, and it wasn't too bad... just had to borrow a wired keyboard.
I installed bluez-utils, and after that the bluetooth setup tool found my keyboard and paired it one go.

Now to restart and test if it still works...

Update:

After a restart I had to re-pair in Mac OSX, but after that, the bluetooth keyboard and mouse both work for Mac and Ubuntu.

Oh, and a big thanks to you ZeroLinux for your post on Lucid fixes for the iMac 10.1, as that fixed a few other problems I was having too.

---

### Post by planetpatrick on 2011-02-15
why what other probes u have?

---

