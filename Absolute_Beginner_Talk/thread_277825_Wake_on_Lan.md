---
title: "Wake on Lan?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by kgls13349 on 2006-10-15
Does anyone have any suggestions as to how to make a ubuntu server built on a Gigabyte GA-K8N51GMF-9 mATX motherboard to boot when it is called on fromt he network using the Wake on Lan feature?

---

### Post by Quintin Riis on 2006-10-15
This has absolutely nothing to do with Ubuntu.

Enable Wake-On-LAN functionality in your motherboard's BIOS, scribble down the MAC address which will be shown by 'ifconfig' when the system is up, then send a "magic packet" to that hardware address from another machine on the same net when you want to power on the machine remotely.

Google will be helpful.

---

### Post by Marsolin on 2006-10-15
There is a [Wakeonlan]("http://linuxappfinder.com/package/wakeonlan") package in Ubuntu that can be used to wake the system up.

---

### Post by kgls13349 on 2006-10-15
i only asked cuz i searched on the net about it and found various articles that mentioned problems with wol with different os`s, including ubuntu and wanted to make sure i set everthing up right,

Thanks for ur replys :)

---

### Post by uraliss on 2006-10-15
I use wakeonlan to boot up my ubuntu server and it works just fine!

well chuffed

---

### Post by Quintin Riis on 2006-10-15
2nd time, for Original Poster and anyone else: it doesn't have anything to do with Ubuntu.  WOL is way before any operating system is loaded.

---

### Post by JayTee on 2006-10-15
I downloaded wakeonlan and used it from my Ubuntu desktop computer to wake up my Ubuntu server. Works great.

To Quintin Riis, no need to be so huffy about the posting. The guy just asked a simple question which easily could have been interpreted as "How do I do this in Ubuntu".

---

### Post by chalex on 2006-10-15
Here is a relevant article: [http://blog.thedebianuser.org/?p=162](http://blog.thedebianuser.org/?p=162)

There's a link to another tutorial in the comments there.

---

