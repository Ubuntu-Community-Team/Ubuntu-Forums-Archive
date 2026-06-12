---
title: "bsnl router through USB port, possible?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-01-05
Dear friends, I have taken ubuntu linux very recently; and one problem looms large. I have no ethernet card; and in windows I used to connect my router through USB port, but in that, my ubuntu does **not** autodetect the ADSL modem on this command:
sudo pppoeconf
Tell me what to do. Can I use it without an ethernet card; or else, have I got to buy it ?

---

### Post by sauravbhaumik on 2007-01-06
Dear friends, I have recently taken Ubuntu. But, a user without an Ethernet card, as I used to connect my ADSL modem through USB port, I now find no way to connect to the web from Ubuntu. Using the command "sudo pppoeconf", I can verify that Ubuntu is unable to autodetect my modem. Advise me what to do.
Regards,
Saurav

---

### Post by lucky_chouhan on 2007-01-06
Your net connection is BSNL so your modem is DSL-502T.:rolleyes:  now why you work through USB i mean connect you modem through Lan because Lan dosen't need any driver.
(Purchase Lan Card It only 150 Rs.)
I have Airtel Connection with Beetel 220Bx and  I use Lan port so in Ubuntu PPPoeconf automatically detect my setting.:)

---

### Post by sauravbhaumik on 2007-01-06
but my modem is Starlite SmartAX MT882. I don't know how to connect the LAN card. Please help me.

---

### Post by lucky_chouhan on 2007-01-06
Ok i found your modem driver for linux.

this is the link try this -

[http://list.driverguide.com/matches.php?h=7e30729c3927477516ae4c953a2f538c&ids](http://list.driverguide.com/matches.php?h=7e30729c3927477516ae4c953a2f538c&ids)[0]=503416&ids[1]=503418&cid=2033&model=MT882


it ask for account so please create dummy account.


or

just plug the ethernet cables in and browse to [http://192.168.1.1](http://192.168.1.1) and configure from there?

---

### Post by logos34 on 2007-01-06
> Can I use it without an ethernet card; or else, have I got to buy it

Depends.  What make and model is your USB ADSL modem?  Some are easier than others.

Even if you can get it working through usb port, I'd still get a nic...they're dirt cheap...it'll be faster and you won't be using as much cpu resources (i.e. the usb controller)

---

### Post by sauravbhaumik on 2007-01-07
Sorry, I can't make a good use of the links. But, take it for granted that I have bought a lan card, how can I connect it? Please instruct me.

---

