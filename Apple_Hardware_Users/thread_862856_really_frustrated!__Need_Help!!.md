---
title: "really frustrated!  Need Help!!"
date: 2008-07-17
forum: Apple Hardware Users
---

### Post by Diggs808 on 2008-07-17
Okay,
Installing 8.04 on Macbook 2,1

No Ethernet
No Wireless

Following the Wiki didn't work.  Reading forums didn't work.  No Joy. 

The lack of Ethernet is due to the crappy sky2 NIC driver.  
Lack of Wireless is due to crappy wireless cards....

I followed the Wiki and cant get that to work.  Even though I did it three times (reinstalling after each failed attempt).  

Can someone please help?

Say what you want to about dell...but I have never had this much trouble getting things to work on my Dell.  This MacBook is a work machine that I want to use Ubuntu on....sigh...

---

### Post by flaggh on 2008-07-17
Take a look at this instructions on this thread:
[http://ubuntuforums.org/showthread.php?t=772836]("http://ubuntuforums.org/showthread.php?t=772836")

They worked for me on my macbook 2,1

---

### Post by cyberdork33 on 2008-07-18
> **Diggs808 said:**
> The lack of Ethernet is due to the crappy sky2 NIC driver.  
Lack of Wireless is due to crappy wireless cards....
sky2 works fine in Ubuntu... Did you have ethernet plugged-in during your install? It probably did not setup networking correctly if not.

Make sure that the sky2 module is loaded:
```
lsmod | grep sky2
```

Check that the interface exists:
```
ifconfig
```
You should see the eth0 device there. If not, then make sure that the following line is in /etc/network/interfaces
```
iface eth0 inet dhcp
```

---

