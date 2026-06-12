---
title: "BT Home Hub Advice"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Risotto on 2006-09-01
Hello everyone

I took the plunge last weekend and now have a PC running Dapper Drake and nothing else.  It's a reasonable spec - AMD 2400+, nVidia 128Mb graphics, 768Mb RAM, 80Gb HDD, CDRW, DVD and Wireless network card (but no modem and not yet connected to the web) - and I'm looking forward to lifting the bonnet(hood) and having a play over the coming months.

I'm currently using BT Broadband on my other PC (Windows XP) - which is also used by my wife so I can't go too wild with that machine! - but it's being upgraded to BT Total Broadband next week.  This means a shiny new Home Hub (wireless router) will be arriving and I can try to connect to the web using the Ubuntu machine's wireless card.

My question is two-fold:
1.  What do I need to do specifically to the Ubuntu machine to make sure the connection via the router works ok?  (I can currently see that a couple of neighbours are using wireless works using the Wireless Assistant function.)
2.  What should I do generally to make sure that my network is secure as I will have both a Ubuntu and an XP machine connected via the Home Hub?

Thanks for any advice!
Mike

---

### Post by xmastree on 2006-09-01
I'm using a BT home hub here, and I just plugged it in and it works. But that wasn't with wireless, I'm using ethernet.
My wife's W98 laptop is wireless, and to conenct that I had to use the WEP key printed on the hub itself to access it.
Without that key I don't think anyone can connect, so in that sense it's secure.

There is a CD with it, but I didn't need that except to look up BT's smtp server.

---

### Post by Risotto on 2006-09-01
Many thanks for this.  Hopefully my installation will be nice and smooth!

---

### Post by Risotto on 2006-09-08
Thanks guys.  Set up the hub and linked it to the XP machine and that's working fine.  Switched over to the Ubuntu machine, updated the WEP key details in System > Administration > Networking and Robert is your father's brother!  Very happy!

---

### Post by xmastree on 2006-09-09
Great! :cool:

---

### Post by ironopolis on 2006-11-16
> **Risotto said:**
> Thanks guys.  Set up the hub and linked it to the XP machine and that's working fine.  Switched over to the Ubuntu machine, updated the WEP key details in System > Administration > Networking and Robert is your father's brother!  Very happy!

Hi I am have a problem with my BT Home Hub and Ubuntu. I have to activate eth1 port before it will connect to the internet. Once I activate it works straight away.
I thought Ubuntu would see the broadband connection and activate it it's self. Or could I activate all the time?

Any help would be much appreaciated.

ironopolis

---

### Post by xmastree on 2006-11-16
Once you activate eth1 it should stay activated.

---

### Post by ironopolis on 2006-11-16
Hi thanks for replying,

it does stay activated until I reboot my system, and then it becomes un-active, and I have to manually activate again ](*,) 

Any ideas on how to fix this problem.

ironopolis

---

### Post by martnemma on 2006-12-09
When you enable the ethernet port did you set it to activate when computer starts? As I believe there is a setting somewhere in the network config. I know there is in Kubuntu.

I'm usung Kubuntu, the BTHomeHub and wireless on all the box's and they all work fine.

---

