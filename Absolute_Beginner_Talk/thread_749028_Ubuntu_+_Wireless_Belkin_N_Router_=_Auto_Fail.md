---
title: "Ubuntu + Wireless Belkin N Router = Auto Fail"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by SkyPioneer on 2008-04-08
Hey guys.
After using Ubuntu dual boot with Windows for a while, the family got a couple of laptops and a Wireless router. The installation disk would not read in Ubuntu (which was quite obvious but I wanted to make sure) so I had to install it with Windows XP.

The Wireless network is up great, both **Vista** laptops read the signal well and, yeah, it works on the **XP** side too. However, when I start it up in Ubuntu, it cannot connect at all, it keeps asking for the password even though I've entered it like 10 times already. I made sure to select WPA Personal (because that is what it is encrypted in) it still refuses to work, forcing me to use a Windows system for about a week now.

The router is a [Belkin N Wireless Router ](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=372043).

Any ideas?

---

### Post by tangibleorange on 2008-04-08
What wireless card are you using? If you don't know, you can try looking for clues in the following commands:

```
lspci
``` if it's an onboard card, or:

```
lsusb
``` if it's a USB card.

---

### Post by SkyPioneer on 2008-04-08
No, you see, it's a PC connected to the router via ethernet. When I click on Wired network that doesn't work, and when I choose the network name it asks for a password and when I type it in correctly, it tells me that it is incorrect.

---

### Post by Mick8882003 on 2008-04-08
Do you have the correct ecription type, hex ect?
Do you have the correct password?
Is capslock on?

that is where I would start.

---

### Post by Mick8882003 on 2008-04-08
oh sorry, your last post didnt sink in.

So your using a wired connection?
same notes for the password, caps ect.

You might want to wait for hardy, has a nework manager built in!
be out in a fortnight.

---

### Post by tangibleorange on 2008-04-08
> **SkyPioneer said:**
> No, you see, it's a PC connected to the router via ethernet. When I click on Wired network that doesn't work, and when I choose the network name it asks for a password and when I type it in correctly, it tells me that it is incorrect.

sorry i'm confused. your wired network needs a password? does WPA extend to wired networks?

---

### Post by louieb on 2008-04-08
Weird:  for an Ethernet wired to Router connection it should be connected when you boot up.  Since its wired no password should be required.

look at these two commands see if there is some clue.
list the network connectors 
```
ifconfig
```and try to get the router to give an IP address.

```
sudo dhclient
```if you could somehow post the output here  it would help.

BTW: when you exit windows don't hibernate. Sometimes that can put you NIC to sleep.

---

