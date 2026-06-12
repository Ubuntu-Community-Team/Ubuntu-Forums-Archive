---
title: "Headache by wireless card finding"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-02-21
hi
from the last two days i am  trying to connect to internet through wireless card in my PC on PCI slot.
Card is Netgear WG311v3.
i am using ubuntu 7.10.
it driving me nuts and dunno how to solve it.
i see network manager,i did not find wireless network there.
I see h/w config and i find that netgear is installed there(driver).
Then i try to run in terminal and to see whether any card is availabe,there also everything is fine.
Just i run this command. i see the following:
> 
iwconfig
lo       no wireless extensions
eth0  no wireless extensions


please any help.

---

### Post by theRightNee on 2008-02-21
run ```
 sudo iwlist scanning 
```

the code above is not super neccessary, i just want to verify that the wireless card is not being recognized at all. if not, you will need to install the drivers for the card using "ndiswrapper.' instructions here:[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-b30aaebf79b1393631b352f8f7a1acf5b17da38c](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-b30aaebf79b1393631b352f8f7a1acf5b17da38c)

have fun =]

---

### Post by mmarif4u on 2008-02-21
thanks for reply.
i try the command u write,i get this:
> lo doesnot support interface
eth0 doesnot support interface

when i tried:
> sudo iwlist
it give me some list.
but i did not see any card there.
what to do further.

---

### Post by theRightNee on 2008-02-21
right...that means you need to install the drivers for your card

refer to the link i put up and follow the instructions. if you have your CD with the windows drivers that will be very helpful, if not you could always download from the website i believe.

this is a howto developed specifically for your card:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29)

hope it helps

---

### Post by mmarif4u on 2008-02-21
ok,i install the .deb files with no problem.
inow i am going to install the inf window driver for card.

when i type in terminal:

> cd ~/home/Inf/WinXP_2K
it says ** NO FILE OR DIRECTORY.**

Even that the route is correct.

---

### Post by mmarif4u on 2008-02-21
@theRightNee

Thank you very much for ur help.
i got it working.

---

