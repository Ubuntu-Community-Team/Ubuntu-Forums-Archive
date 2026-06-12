---
title: "Unable to save power on MBP 5,3 / Natty"
date: 2011-05-08
forum: Apple Hardware Users
---

### Post by Silmathoron on 2011-05-08
Hi everyone. I've seen quite some threads about saving power with ubuntu in order to make the battery last more than 5 hours.
However, I've got a MBP 5,3 with a GeForce 9600M GT (I can't use the 9400M), running Natty 64bit and I have been unable to make it last more than 2h30.

I've looked on these threads [http://ubuntuforums.org/showthread.php?t=1215928&highlight=save+power](http://ubuntuforums.org/showthread.php?t=1215928&highlight=save+power), [http://ubuntuforums.org/showthread.php?t=1170477&highlight=save+power](http://ubuntuforums.org/showthread.php?t=1170477&highlight=save+power) and others and here is what I came up with :
[LIST]
[*]I'm using laptop-mode
[*]I underclocked my GPU nearly to minimum
[*]I've got the backlight at minimum power
[*]I set the 2 CPU to ondemand and limited their speed to "medium" on battery
[*] I set the usb to autosuspend
[*]I use the attached script on login
[/LIST]

Still, according to powertop, my consumption is always over 17W on battery

I'm kind of depressed : where on earth does all that power go ? How can I find out ?

Here are my lspci, my script and a typical powertop

---

### Post by Silmathoron on 2011-05-10
up.
Anyone reporting from a 5,3 ? On the help page, they say the battery can last up to 4h... [https://help.ubuntu.com/community/MacBookPro5-3/Natty](https://help.ubuntu.com/community/MacBookPro5-3/Natty)

---

### Post by samuaz on 2011-05-10
This problem occurs because the kernel 2.6.38 which has a bug that reduced 20-40% the battery life and causes overheating in some laptops.

apparently the new kernel 2.6.39-rc7 also drag this bug

hopefully they can fix it before leaving the stable version of the new kernel.

[http://ubuntuforums.org/showthread.php?t=1745389](http://ubuntuforums.org/showthread.php?t=1745389)

[http://www.phoronix.com/scan.php?page=news_item&px=OTM3NQ](http://www.phoronix.com/scan.php?page=news_item&px=OTM3NQ)
[http://ubuntuforums.org/showthread.php?t=1739770&page=3%22](http://ubuntuforums.org/showthread.php?t=1739770&page=3%22)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

Battery life its 1-2 hours more in mac osx

---

### Post by Silmathoron on 2011-05-11
Okay, that's a relief, at least it means that it will eventually be fixed. Thanks a lot mate, guess we'll just have to wait...

---

