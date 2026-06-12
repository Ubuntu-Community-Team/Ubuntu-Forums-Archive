---
title: "MacBook 3,1 Cannot Connect To Secure Network"
date: 2008-09-05
forum: Apple Hardware Users
---

### Post by Coder543 on 2008-09-05
So i've had my MacBook (3,1) for a few months and have been thoroughly enjoying it. Since this was my first mac I had to learn how to use it effectively. I learned it. Now to learn more i've partitioned it and installed ubuntu. The only problem that I now have with ubuntu is that it cannot connect to my wpa-aes secured home network (hidden). It is able to connect to unprotected networks easily, but fails miserably when connecting to my home network. Can anyone help me? This is the only flaw i've seen in ubuntu. If this gets fixed it would be very good.

Stats:
MacBook 3,1
2 gb RAM
250 gb Hard Drive

---

### Post by cyberdork33 on 2008-09-05
A lot of people have been complaining about this again recently. I think there is a bug somewhere again.

What driver are you using? Have you tried with others?

Have you tried wicd in place of network-manager?

---

### Post by Coder543 on 2008-09-06
Yes, i've tried Wicd, to no avail. I believe I am using ndiswrapper...

EDIT: and i've tried others with no result.

EDIT2: I do not know if this would be helpful for anyone in finding the bug related to the WPA.. but the router tools indicate that I *do* join the network, only to disassociate moments later... Perhaps this is a simpler bug than it might yet have been? (Router tools being the tools for my router)

---

### Post by hanzomon4 on 2008-09-06
Ndiswrapper won't connect to protected networks, not sure why. Try the ath9k driver, you will be able to connect to protected networks but not unprotected networks.

---

### Post by Coder543 on 2008-09-06
Would the atk9k driver work on a non-pro macbook with a broadcom?

---

### Post by hanzomon4 on 2008-09-06
Well I if it's an atheros card.... Are they broadcoms

---

### Post by Coder543 on 2008-09-06
I think it is...
This is what the mac utility system profiler outputs about what kind the card is: Broadcom BCM43xx 1.0 (4.170.46.9)

---

### Post by cyberdork33 on 2008-09-06
Broadcom != Atheros. (Those are the two companies' names).
[http://www.atheros.com/](http://www.atheros.com/)
[http://www.broadcom.com/](http://www.broadcom.com/)

ndiswrapper is the only driver solution for Broadcom cards in Macs.

---

### Post by Coder543 on 2008-09-07
Is there anyway i can connect to a protected network, my macbook needs protected networks more than unprotected right now.

---

### Post by Coder543 on 2008-09-08
As of now i have done further research and found that wep is functional. It would appear that WPA needs help... Advice anyone?

---

### Post by johnlocke2342 on 2008-09-22
Hello.
I've got the same problem with my MacBook 4.1. Anybody help?

---

### Post by cyberdork33 on 2008-09-22
> **johnlocke2342 said:**
> Hello.
I've got the same problem with my MacBook 4.1. Anybody help?
Please start a new thread and go into more detail about what is working and what is not.

---

