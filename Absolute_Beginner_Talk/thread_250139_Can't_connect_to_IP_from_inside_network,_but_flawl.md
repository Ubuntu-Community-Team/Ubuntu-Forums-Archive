---
title: "Can't connect to IP from inside network, but flawless outside of network..."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-09-03
This has me stumped.  Why is it that I cannot access my server by typing my public IP from WITHIN my network? 

When I'm on a computer outside my network, it works flawlessly...
](*,)

---

### Post by kc5hwb on 2006-09-03
Are you talking about the RDesktop (Remote Desktop) package?  Is this what you are using to connect?  Because I am having the same issue, I cannot connect to my Ubuntu box from within my network using RDP.

---

### Post by baylorbear on 2006-09-03
> **kc5hwb said:**
> Are you talking about the RDesktop (Remote Desktop) package?  Is this what you are using to connect?  Because I am having the same issue, I cannot connect to my Ubuntu box from within my network using RDP.

Not actually.  I've got Apache2 up and running and it works fine if I reference my server as [http://localhost/](http://localhost/) from my box -- or using my internal IP from another computer inside the network: 192.168.0.2

Outside my network, I can access my server by typing my public IP address...  

But inside, I can only access it via [http://localhost/](http://localhost/) or [http://192.168.0.2](http://192.168.0.2)   --  [http://my.ip.add.ress/](http://my.ip.add.ress/) returns a "host not found" message.

---

### Post by steve.horsley on 2006-09-03
This is to be expected. Your router is performing address translation for incoming connections (WAN->LAN) and also for outgoing connections (LAN->WAN). But you are trying to go a rather strange route, to a public address, LAN->WAN except that the public address is only visible for WAN->LAN, and LAN->LAN doesn't get translated. Don't ecpect to be able to connect to the pubic address from inside - it ain't going to happen.

---

### Post by baylorbear on 2006-09-03
> **steve.horsley said:**
> This is to be expected. Your router is performing address translation for incoming connections (WAN->LAN) and also for outgoing connections (LAN->WAN). But you are trying to go a rather strange route, to a public address, LAN->WAN except that the public address is only visible for WAN->LAN, and LAN->LAN doesn't get translated. Don't ecpect to be able to connect to the pubic address from inside - it ain't going to happen.

Ahh!  The explanation I've been looking for!  Thank you for the insight!  I was wondering if it was possible or whether I was attempting the un-doable...

---

