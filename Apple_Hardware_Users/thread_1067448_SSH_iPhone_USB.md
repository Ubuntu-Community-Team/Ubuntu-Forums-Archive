---
title: "SSH iPhone USB"
date: 2009-02-11
forum: Apple Hardware Users
---

### Post by tygoerlitz on 2009-02-11
Does anyone know if there is a way to ssh into the iphone 3G in ubuntu. The primary reason to do this is because i want to try and use the internet from my iphone on my comp, since i dont have a wireless card. Please help!

Thanks

---

### Post by Hobgoblin on 2009-02-11
I think you are thinking about it the wrong way.

You want to use your iPhone as a 3G modem?

---

### Post by punx45 on 2009-02-11
you have to jailbreak the phone, and install openSSH on it.   you can then tunnel to it and use it as a proxy.   most tutorials i have seen use an ad-hoc wifi network to achieve this so you may be out of luck.   i have seen a couple using the USB cable but they involved windows programs which i assume dealt with communicating over the bus.   you can try some googling and see if anything else turns up.

---

### Post by tygoerlitz on 2009-02-11
ok thanks. Yes I am trying to use my iphone as a 3G modem since I dont have a wireless card in my ibook.

---

### Post by Legolover64 on 2009-02-12
Once you jailbreak your iPhone, go into Cydia. Find "PdaNet" and install it. Create an ad-hoc wireless network on your computer, join it with your phone, and start PdaNet. It has all the daemons and everything running to make it all "just work" and you'll be tethered in no time :)

---

### Post by tygoerlitz on 2009-02-12
Ya i would do that but i dont have a wireless card in my laptop

---

### Post by cyberdork33 on 2009-02-12
I believe that doing this over USB only works in Windows currently.

You might want to read up on SSH. SSH is something you do over a network connection... so you would have to have a network connection on both the iPhone and your computer in order to "ssh in" to your iPhone.

---

### Post by togume on 2010-09-08
Sorry to revive this, but this does in fact work: [http://ubuntuforums.org/showthread.php?t=1570791](http://ubuntuforums.org/showthread.php?t=1570791)

@cyberdork33 - :P

---

### Post by gb@ssan on 2010-11-25
Hi

There is a simple solution to do this. Check it out in the following link: [http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html)

I am using my 3Gs iPhone as 3g modem for the last 6 months with my 10.04 - 10.10 ubuntu.

Regards.

---

