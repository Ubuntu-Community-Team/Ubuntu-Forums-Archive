---
title: "Big problem whith USB"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by stemcfly on 2006-11-01
Hi all..I'm an ubuntu newbe from Italy.. I've got a very big problem with my usb ports..
I enter ubuntu and after 1 or 5 or sometimes 10 minutes all my usb ports stops working.. I don't know why.. :( ..I tried a lot of things(to change mouse, to change video drivers, to change options..all..)..but nothing..and I noticed that with live version(and also with both ubuntu edgy and kubuntu) I've got the same problem..

Os. vers: Ubuntu 6.06
Mouse: trust optical
Pc: fujitsu siemens amilo laptop

Is someone able to help me??

Thanks a lot!! ;)

Sorry mods.. double post..

---

### Post by xyz on 2006-11-01
Try to run the following command line in a console:
```
tail -f /var/log/messages
```
As you do it, you have to leave the window open and plug in your USB and see what it says.

---

### Post by stemcfly on 2006-11-01
> **xyz said:**
> Try to run the following command line in a console:
```
tail -f /var/log/messages
```
As you do it, you have to leave the window open and plug in your USB and see what it says.
ok.. I've just done..
Usb stopped working.. then i ran that command above.. and this is the output:
---
Nov  1 15:40:19 localhost kernel: [17180139.012000] usb 2-1: USB disconnect, address 2 [COLOR="Red"]//I plugged off my mouse[/COLOR]
Nov  1 15:40:23 localhost kernel: [17180143.012000] ohci_hcd 0000:00:13.1: IRQ INTR_SF lossage
Nov  1 15:40:24 localhost kernel: [17180144.372000] usb 1-1: new low speed USB device using ohci_hcd and address 2 [COLOR="Red"]//I plugged on my mouse[/COLOR]
Nov  1 15:40:25 localhost kernel: [17180145.372000] ohci_hcd 0000:00:13.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ. [COLOR="Red"]//I think this is the error..[/COLOR]
---
What should I do now??

Thanks A LOT man! ;)

---

### Post by xyz on 2006-11-02
Try these 2 links and see if you can work it out:
[USB not detected]("http://ubuntuforums.org/showthread.php?t=150804")
[ usb devices not detected in Ubuntu 6.06]("http://www.linuxquestions.org/questions/showthread.php?t=463119")
Hope it works.

---

### Post by t0mc4t on 2006-11-07
I have the same problem with my laptop using ATI 200M motherboard.
My USB mouse is stop working after several minutes of usage.
Does anyone know the solution of this problem?

---

### Post by louieb on 2006-11-07
The problem sound like an IRQ conflict. An example of something that could create such a situation is alternating the use of the touch pad on the laptop and using a mouse plugged into a PS2 port. Signals get crossed, the computer gets confused. This use to be a big problem before PCI cards and USB ports. There are only a limited number of IRQs 15 or 16 and 3 or 4 of those are reserved.  Newer computers are good at auto detecting hardware and assigning IRQ's. 
I don't know if you have an external keyboard or mouse plugged in.
But if you do disable the mouse / keyboard on the laptop when you use the external one and see if the problem stops.

---

### Post by t0mc4t on 2006-11-07
How to disable the touch pad?
Anyway, I read from other posting, it said that we can used "noapic acpi=off pci=noacpi irqpool" in the boot kernel to fix it..
Does anyone know why we have to do that to fix it?

---

