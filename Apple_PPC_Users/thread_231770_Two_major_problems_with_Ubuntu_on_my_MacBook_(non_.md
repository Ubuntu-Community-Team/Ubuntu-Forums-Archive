---
title: "Two major problems with Ubuntu on my MacBook (non Pro)"
date: 2006-08-07
forum: Apple PPC Users
---

### Post by Entity on 2006-08-07
I followed theses [steps]("http://bin-false.org/?p=17") in order to install Ubuntu on my new MacBook Black (which is non Pro as you probably know) and now I have two major issues..

1) I keep getting kernel panics on system startup. I can simply reboot and then everything is fine but it's a pain.

2) When coming opening the macbook's lid in order to wake it up from sleep the screen stays black and I have to reboot the machine. I tried the default setup and also the setup according to the instructions [here]("http://bin-false.org/?p=17") and get the same problem in both cases.

Any ideas regarding these?

---

### Post by louistan3 on 2006-08-07
ive never used macbooks before but i thnk laptops have a hibernation problem.. i saw some threads before about fixing the hibernation.. try searchin for them.. hope this helps.. :)

---

### Post by chasisaac on 2006-08-08
> **Entity said:**
> I followed theses [steps]("http://bin-false.org/?p=17") in order to install Ubuntu on my new MacBook Black (which is non Pro as you probably know) and now I have two major issues..

1) I keep getting kernel panics on system startup. I can simply reboot and then everything is fine but it's a pain.

2) When coming opening the macbook's lid in order to wake it up from sleep the screen stays black and I have to reboot the machine. I tried the default setup and also the setup according to the instructions [here]("http://bin-false.org/?p=17") and get the same problem in both cases.

Any ideas regarding these?

1. I hate to say this (reinstall)
2. Hibernation is a real pain. Check out  [http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)

---

### Post by Entity on 2006-08-09
> **chasisaac said:**
> 1. I hate to say this (reinstall)
2. Hibernation is a real pain. Check out  [http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)

1) You don't have kernel panics???
2) I tried to "... edit /usr/sbin/laptop-detect and insert a line 'exit 0' right after the #!/bin/sh ..." but not luck. I also tried [this]("http://bin-false.org/?p=17") (Comment 139) without success also.

What have you done to get yours working?

---

### Post by jedsen on 2006-08-10
Are you talking about hibernation or suspend? Both are broken on the macbook. The failure to resume video on "lid-open" is a strange problem with an ugly hack that has been merged to the kernel (or was waiting to be merged as of June). The hibernation, I don't know about, but it looks like it could be a similar problem.

You need vbetool with the ugly suspend hack to get it to work, so if you don't have it installed, do so, and see if that works (but don't hold your breath).

Those kernel panics are "normal", there's a patch out there waiting to be merged into the kernel.

---

