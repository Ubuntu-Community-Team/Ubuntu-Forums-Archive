---
title: "Problems running ADSL USB Modem 6205 under Ubuntu 7.04"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Kaphius on 2007-04-30
Greetings. I recently transfered from WinXP to Ubuntu 7.04 at home (I already work with Ubuntu in the office). My internet connection is with an Asus 6205 Modem Zhone Technologies ADSL USB Modem, but there seems to be some problem loading the unit. I can see it in the hardware list, but it doesn't load. Could someone help me in the configuration of the unit. Thanks!!!

---

### Post by oilchangeguy on 2007-04-30
what do you mean, it doesn't load? you can't get on the internet? ubuntu is not a big fan of usb to modem connections. does the modem have an ethernet connection? if so, i suggest you use that.

---

### Post by starcraft.man on 2007-04-30
> **Kaphius said:**
> Greetings. I recently transfered from WinXP to Ubuntu 7.04 at home (I already work with Ubuntu in the office). My internet connection is with an Asus 6205 Modem Zhone Technologies ADSL USB Modem, but there seems to be some problem loading the unit. I can see it in the hardware list, but it doesn't load. Could someone help me in the configuration of the unit. Thanks!!!

It might require specific USB drivers to run your internet across it, doesn't your modem come equipped with a ethernet port in the back. I can't imagine that they only gave you a USB plug. I don't think there is a noticeable difference between USB or Ethernet to get your internet. I'd plug in the ethernet. If you don't have an ethernet plug on the modem, you can always get a router (I'd recommend LInksys I like them, Belkin good too) that has a USB plug and then wire an ethernet line right to your computer. (It is strongly recommended to have a NAT router on your home connection anyway to prevent worms and other malicious web problems, a router is the best firewall you can ever get for a computer)

---

### Post by Kaphius on 2007-04-30
OK. The internet ADSL connection is done through a filtered phoneline, but the only connection from the modem (only one usb port, no ethernet at all) to the computer is via USB.  At my office (the computer I'm actually  writting this at) is connected via ethernet, and it works fine. There are some people who have had success in making an usb modem work, so I wonder if anyone has any good ideas as to how to get it going.

---

### Post by oilchangeguy on 2007-04-30
i suggest you check with your isp to see if they can provide you with a modem that has an ethernet connection.

---

### Post by Kaphius on 2007-04-30
They can, but it'll cost about $15.00 per month extra on my phone bill. I'd rather see if I can get this unit running before having to cash-in the extra dough for the ethernet unit.

---

### Post by oilchangeguy on 2007-04-30
check this out:
[http://www.newegg.com/Product/Product.asp?Item=N82E16825120101&CMP=KNC-GoogleAdwords&ATT=Networking](http://www.newegg.com/Product/Product.asp?Item=N82E16825120101&CMP=KNC-GoogleAdwords&ATT=Networking)

---

### Post by Kaphius on 2007-04-30
OK. Maybe I should clear some things up. 

First: The actual unit does not have an IP assigned. It is assigned by the SysAdmin at Cable and Wireless, and from there the unit by itself connects, and then supplies the internet feed to the computer.

Second: I live in Panama, central america, so please don't send my any computer supply webpage since it would probably be more hassle than worth.

Third: In case you wonder what unit I'm talking about, take a look at this page:

[http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport](http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport)

Look at the modem labeled: ASUS AAM6000UG

---

### Post by starcraft.man on 2007-04-30
Hmmm, right I get your situation. I still think there are routers out there that take an input of USB internet and let you hook a ethernet out of it, I'm sure I've seen that somewhere. Maybe you should check your local hardware store for some such router, then you won't need to pay a monthly fee. Sounds to me like thats your best solution, not to mention you should always have a router on your connection, provides hardware firewall protection and stealths you from the internet.

As for your exact model working directly as USB into Ubuntu, can't say I've ever seen anyone else post about that specific model.

---

