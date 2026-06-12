---
title: "Installing Ubuntu problems"
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by PaulWiggers on 2005-06-30
Hello,

Well the time has come to install ubuntu. I have backed up all my files, created 50gb for linux and made 110gb fat32.

But at the installation i immediatly run into a problem. When I boot, and press enter (to default install) the kernel boots, it gives me different messages which are supposed to be there i assume. But when it reached the message

OHCI_HCD 0000:00:03.1: new usb registered, assigned bus number 2

the system freezes. I cannot continue the install.

What can I do to solve this?

Tia

Paul

---

### Post by PaulWiggers on 2005-06-30
Ok, that problem was solved by using the line

linux debian-installer /probe/usb=false

but now i run into another problem. The installation is completed and it has to reboot, when it get to the line

starting hotplug subsystem

the system freezes again. 

How can this be solved? Do i need to enter some extra commands when booting?
if so, can this be added in some kind of boot file so that i don't have to type it everytime that i boot the system?

thanks in advance

Paul

---

### Post by az on 2005-06-30
I am a really lazy person.

I would first take a look at the hardware that is on you usb system.

If you have nothing plugged in, then the usb controller may be hogging an irq or doing something esoteric,  Can you change the usb settings in your bios?  If not, can you disable usb completely?  If you can you can boot and take a look at the past kernel logs to see what made your system crash.

When you can boot your system, you can look in /var/log and see what happened.   There is certainly a module you can blacklist in hotplug which wil allow you to continue, but that _may_ leave you with reduced or absent usb functionality.  It would be best if te problem can be fixed in the bios level.

---

### Post by PaulWiggers on 2005-07-01
Thanks,

I disabled the usb controller in the bios, installed, then enabled it again and now it works.

Just can't seem to get my internet working under ubuntu. My network card is recognized. I have configured the card and activated the connection. But it doens't work.

Any idea's on how to fix this?

I have 

sis 900-Based pci fast ethernet (network card)
speedtouch 510 broadband modem

---

### Post by poofyhairguy on 2005-07-01
Its the modem. Look here:

[http://www.ubuntuforums.org/showthread.php?t=5879&highlight=speedtouch+510](http://www.ubuntuforums.org/showthread.php?t=5879&highlight=speedtouch+510)

[http://linux-usb.sourceforge.net/SpeedTouch/](http://linux-usb.sourceforge.net/SpeedTouch/)

to get it to work.

---

### Post by PaulWiggers on 2005-07-01
I don't hava an usb modem. My modem is connected to my computer through the ethernet card.

Is that another procedure or wil it work just the same?

---

### Post by PaulWiggers on 2005-07-01
I have followed the howto, but that seems to be for usb modems as well, therefor i still haven't succeded in getting up my internet

please offer some suggestions

tia

---

