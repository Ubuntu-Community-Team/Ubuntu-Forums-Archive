---
title: "Status of Wireless for MacBookPro8,2"
date: 2011-10-22
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2011-10-22
What is the status of Wireless for the somewhat new MacBook Pros?

I'd like to get wireless networking up and running if it is supported.
Here is part of the output of **lspci -nn**
```

02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
```

I'm not finding anything listed inside the Network Connections -> Wireless utility.  Are there special drivers that have to  be installed as a work-around?

---

### Post by rfkrocktk on 2011-12-28
Here's where we're at: [http://delicious.com/redirect?url=http%3A//homepage.uibk.ac.at/%7Ec705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://delicious.com/redirect?url=http%3A//homepage.uibk.ac.at/%7Ec705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

Works fine for me on 8,3 MBP, but I do lose internet connectivity (not network connectivity) every so often.

---

