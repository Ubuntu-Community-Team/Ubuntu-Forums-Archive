---
title: "Wireless networks don't appear"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by rookybeats on 2008-02-15
I'm using an Edimax 7318UG wireless card

[IMG]http://www.gudangnetwork.com/gnet/components/com_virtuemart/shop_image/product/2a51d8952f49fce4c15c95c4acc12a94.jpg[/IMG]


I've recently installed Ubuntu, and it works great. It's very stable, and fast too.

But, one problem is, that when I click the network list at the top bar, under "Wireless Networks", nothing shows up. 4 Network SSIDs should be in the list, but there's nothing there:confused:

Even if I enter details manually, it won't connect.



I've used recovery mode, and it's the same.


I have the CD for the drivers in my hand now, but I'm not sure how to run it in Ubuntu.

It worked once a while ago, but stopped again soon after.

:(

---

### Post by uberlube on 2008-02-15
Ubuntu and Linux in general only natively support a few number of wireless drivers out of the box. The good news is that you have the windows driver on cd and there is a program in the repositories called 'ndiswrapper' that extracts the firmware from the driver and installs it. I had the same problem with my Broadcom wireless drivers and I used the method on this site:
[http://forums.fedoraforum.org/printthread.php?t=174265]("http://forums.fedoraforum.org/printthread.php?t=174265")
This forum will at least give you an idea of how to work the ndiswrapper in the command line, although you will have to replace the bcm43xx driver with your own.

Checking the Wikki for Ubuntu wont help either, they may have instructions for wireless flash cards.
Hope this helps.

---

### Post by xc3RnbFO8P on 2008-02-15
> It worked once a while ago, but stopped again soon after.

Do you dual boot (windows)?

If you do, use windows to "warm it up" and then restart.

Sometimes it helps to change usb port.

---

### Post by uberlube on 2008-02-15
This thread is specific for you stick:
[http://ubuntuforums.org/showthread.php?t=279946]("http://ubuntuforums.org/showthread.php?t=279946")

---

### Post by decoherence on 2008-02-15
That device uses the ralink chipset, the drivers for which are 'hit and miss' in Gutsy. I've gone through three devices and found extremely inconsistent behavior with each of them. That is to say, they were consistently inconsistent. Sometimes they would connect for a few minutes, sometimes they'd see the network but refuse to connect, sometimes they wouldn't see the network, sometimes the devices wouldn't be recognized at all!

The good news is that this appears to be fixed with the next version of Ubuntu. All my Ralink gear now works perfectly. It's kind of shocking (still, lots of other stuff is broken. I'm not suggesting you upgrade before the release.)

Search around for 'serialmonkey' and 'ralink' ... there are a couple of howtos and I've had varying degrees of success with them.

If you want to use the drivers that came on the CD, which may be easier, check out NDISwrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by rookybeats on 2008-02-15
Thanks for the help guys, although alot of the suggestions here require me to be connected to the internet:S

---

