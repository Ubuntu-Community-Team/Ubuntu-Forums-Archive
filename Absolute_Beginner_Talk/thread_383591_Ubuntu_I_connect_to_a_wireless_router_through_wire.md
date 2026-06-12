---
title: "Ubuntu: I connect to a wireless router through wireless card but I have no internet."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by spahar on 2007-03-13
Ok guys here is the deal. I just installed Ubuntu in my laptop. I have a wireless card, which I enabled through the Network System.

Now i type in the terminal the command:

> iwlist ra0 scan

and I get a list of all the available network.

After that I type:

> iwconfig ra0 ap [AP Address]

and I get connected to the network, the card's led light up and I assume everything is ok.

But I can't access the Internet nor from the Firefox, neither from the Terminal. Why??

I would like also to say that from windows I can connect to the same network and everything is fine. So any ideas that may help are apreciated, cause without this I cannot get the updates for Ubuntu.

---

### Post by jdfreshwater on 2007-03-13
Have you checked the ip address that you have through ifconfig to see if you are getting a proper ip address.  You may also want to try to ping your router....ie ping 192.168.1.1 .  Also make sure that your laptop has the wireless turned on, most laptops now have a button to turn on wireless.  If this button is not pressed, the wireless will not work.

---

### Post by spahar on 2007-03-13
> **jdfreshwater said:**
> Have you checked the ip address that you have through ifconfig to see if you are getting a proper ip address.  You may also want to try to ping your router....ie ping 192.168.1.1 .  Also make sure that your laptop has the wireless turned on, most laptops now have a button to turn on wireless.  If this button is not pressed, the wireless will not work.

The wireless should be ok, cause I connect to the router and also the leds of the wireless card light up. I'll try the ping thing and i'll check the ip, I'll report back here, thx.

---

### Post by spahar on 2007-03-13
Ok I'am gonna need some help here, can you please tell me the exact command in order to see if  I get an IP???

---

### Post by spahar on 2007-03-14
Ok, I think you are right, I don't get an IP address. I run the command Ifconfig but in the ra0 interface, there is not a line with the inet addr and Mask, as I supposse it should be.

So now what, what is wrong??

---

### Post by ricardisimo on 2007-03-14
What distribution are you working with? Dapper? Edgy? Please don't say Feisty...

---

