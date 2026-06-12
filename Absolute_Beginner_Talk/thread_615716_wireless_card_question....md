---
title: "wireless card question..."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by josh air balloon on 2007-11-17
I have a Dell Wireless 1390 WLAN Mini Card Rev 3.6 and it is picking up 2 wireless networks, one password protected, and one not.  I try logging in to the one that is not protected, and the symbol for logging in (the 2 swirling dots) just keeps showing up and, eventually, it stops and the 2 computers with the x shows up.

It seems like the card is finding signals, but it cant log on to the wirless network, what is wrong?

---

### Post by Harpoon on 2007-11-17
It could be that the signal stength is insufficient, or the wap may have enabled MAC access control

Post more info about what feedback you are getting and someone will be able to help you troubleshoot if there is a problem

---

### Post by josh air balloon on 2007-11-17
What kind of "feedback" can i post??

---

### Post by teryowen on 2007-11-17
If you've installed ubuntu, then find and run the restricted drivers program which comes with the installation hook up your laptop to an ethernet cabke get a connection to the net and using the restricted drivers program you should have an option for bcm43xx which after you go through the process should work.

---

### Post by daimaru on 2007-11-17
its most likely what harpoon said your have mac address control enabled in your router and ubuntu choose a different ip for your card meaning your router has your mac stored with ip 192.168.1.22 for example and dhcp assigned you 192.168.1.11 or something so it dont work.
EDIT:
just do a 
```

sudo ifconfig <wifi-interface> 192.168.1.<right number> up 

```

---

### Post by mdpalow on 2007-11-18
Is the ESSID password protected? If so, did you put in the right settings and password?

As an example, did you select WEP 64/128 Hex and then put in your password?

---

