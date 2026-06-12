---
title: "Firewire on iMac G3 no longer working"
date: 2010-08-21
forum: Apple Hardware Users
---

### Post by rquint on 2010-08-21
I'm not sure if I have a hardware or OS problem.  Firewire on my old G3 iMac has stopped working.  Previously I've used a scanner and an external hard drive (Iomega eGo) without problems while running Lucid.  Now neither works with the iMac, though they both work when connected to a PC.  Both the PC and the iMac are running the latest versions of Lucid.  

I can't tell when the problem began since I don't use the scanner or hard drive that often.  I did try booting using the live 10.04 CD for PowerPC and had no joy with either device.

The LCD on the hard drive lights when connected to the firewire port so power is coming through. The scanner has its own power supply.

Checking with lsmod I see that both the modules ieee1394 and ohci1394 are loaded.

I suspect it's a problem with the hardware. Does any one have an idea how I can go about verifying that?  I'd hate to bin an old faithful without first checking everything out.

---

### Post by linuxopjemac on 2010-08-22
Easy if you have OSX still installed. Then you can check from within OSX if it works.

---

### Post by rquint on 2010-08-22
Alas, that's not possible.  It was rescued from the scrap heap with a dead hard drive that I replaced.

---

### Post by rquint on 2010-08-25
Problem solved.  Found the answer at 

[http://discussions.info.apple.com/message.jspa?messageID=10736510](http://discussions.info.apple.com/message.jspa?messageID=10736510)

the overload protection for the FireWire ports has tripped.

Similar to the SMC article, there is also another article here that suggest's a slightly different method for resetting the port protection and getting them back in service.

1. Shut down the computer.
2. Disconnect all devices and all other cables, except the keyboard and mouse cable(s).
3. Disconnect the computer from the power outlet and wait for 3 to 5 minutes.
4. Plug the computer back in and turn it on.
5. Reconnect the device(s) (one at a time if there is more than one) and test. Test with each port if you have more than one.

---

### Post by cottasofia on 2010-08-26
I have a three-year-old iMac G5 that had a problem since I bought it  that I've only just got to the bottom of - its fans would start up about thirty seconds after I shut it down. Nearly every time. I  think I disabled it from going to sleep pretty soon after I got it, but  I vaguely remember it not recovering from sleep and the fans coming on  randomly.

---

