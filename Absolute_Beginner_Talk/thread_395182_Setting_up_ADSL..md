---
title: "Setting up ADSL."
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by STCC on 2007-03-27
Hi, 

I'm extremely noobish at linux, could anyone please direct me to some instructions on how to set up wired ADSL in ubuntu. I'm really struggling to get it working.

---

### Post by STCC on 2007-03-27
Sorry to double post but in windows you can just type in the IP address in a browser and the settings for the modem come up. Is there a way of doing this in linux? As simply typing in 192.168.1.1 does nothing. 

Also i am not at all sure what a "gateway" is is this just the same as my IP address?

---

### Post by halitech on 2007-03-27
setting a dsl connection will vary depending on the provider. Do they use PPPoE or do you have a router or is it a straight connection?

---

### Post by STCC on 2007-03-27
PPPoE.

I have a Netcomm NB13000 plus 4 modem and a Realtek 8139 D network card.

---

### Post by halitech on 2007-03-27
try opening a terminal and running

```

pppoeconf
```

---

### Post by STCC on 2007-03-28
That's exactly what i was looking for but it says sorry i scanned 1 interface, but the access concentrator of you provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem. 

Any idea what's wrong?

---

### Post by digital_sabotage on 2007-03-28
Newbie here too ...but can't you configure from >System>Administration>Networking?  Any detected connections should show there

---

### Post by STCC on 2007-03-28
Yeah i've tried that and typed in all the data that my computer uses in windows to set up the network but it's still not working.

Is there a way of checking if my modem is installed? Cause i doubt it is cause typing in the IP address in firefox doesn't work.

---

### Post by kostkon on 2007-03-28
STCC as I can see you have a modem-router-switch. Thus, the PPPoE connection is done by the modem and is indepedent of the OS you run. So, the problem you have is a network connection problem; for some reason in Ubuntu your lan card is not working/recognised and you cannot access your modem or get internet connection from that. Did you seacrh the forums here to find info about your network card (the Realtek 8139 D) or maybe does someone know anything about this card?

I hope I helped you somehow...

---

### Post by kostkon on 2007-03-28
STCC try to go at **System -> Networking** and see if there is an *Ethernet Connection* option in the list and see if you can activate it.

---

### Post by STCC on 2007-03-28
My network card seems to work, there's an option and i've enabled it, i've also fooled around with the static IP setting and if i ping 192.168.1.1 which is my IP i get results but somethign just isn't working... 


Can anyone suggest a method for finding out the address of my router cause the only thing that can be wrong is the "gateway" which i have now learned should be my router address.

---

### Post by STCC on 2007-03-28
I typing this message through firefox in Ubuntu, thanks a lot for the help. In the end the problem was i had my Gateway as my ip and my IP as my gateway lol.

---

### Post by kostkon on 2007-03-28
Happy that your problem was solved. :-D

---

### Post by Cloudy on 2007-03-28
> **STCC said:**
> I typing this message through firefox in Ubuntu, thanks a lot for the help. In the end the problem was i had my Gateway as my ip and my IP as my gateway lol.

I'm sure you know by now, but it doesn't hurt to reinforce - your gateway address is the equivalent of your Default address in Windows.

---

