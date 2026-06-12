---
title: "Absolute Ubuntu Linux Noob: WPA Wireless"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by MilenkoD on 2007-05-29
I succesfully instlled 7.04 on my Thinkpad T30.  I have a Cisco Aironet card that I'd like to use.  My home wifi router runs WPA.  The Aironet card is recognized but only offers WEP encription.  How do I get WPA?

I'm a total noob at Ubuntu and linux.  I have no clue what I'm doing when it comes to installing anything in this environment.

---

### Post by seshomaru samma on 2007-05-30
I might be wrong but I believe the Cisco drivers don't support WPA
from Cisco's website ([http://www.cisco.com/en/US/products/hw/wireless/ps458/products_qanda_item09186a008019bd57.shtml](http://www.cisco.com/en/US/products/hw/wireless/ps458/products_qanda_item09186a008019bd57.shtml)**)**:
> Q. Does the Linux driver for the Cisco Aironet 350 Series Wireless Card support Wi-Fi Protected Access (WPA) encryption?

    A. No, the Linux drivers for the Cisco Aironet 350 Series Wireless Card do not support WPA. 

maybe there is another way to solve it but I am not aware of any...

---

### Post by seshomaru samma on 2007-05-30
post number 12  in[ this french forum ]("http://forum.ubuntu-fr.org/viewtopic.php?pid=945281")claims that you need to update the firmware and then you can have WPA support

---

### Post by vanadium on 2007-05-30
Just use WEP eventually. It is enough to keep the honest or inadvertent people out. Perhaps the place would be a better world if everybody left their wireless open: we could all surf wherever we are (in the cities, that is).

---

### Post by george29 on 2007-05-30
> **vanadium said:**
> Just use WEP eventually. It is enough to keep the honest or inadvertent people out. Perhaps the place would be a better world if everybody left their wireless open: we could all surf wherever we are (in the cities, that is).

the reason people use encryption algorithms is stop people getting hold of information that they shouldn't - using WEP is not a good solution... if someone decides to, they could grab all sorts of information from the communication between router and wireless computer, e.g. passwords, banking details etc. 

people have wifi as it allows them to be free from wires - if everytime you want to do something like online banking you have to plug in a wired connection, you lose all the benefits of wifi and might as well not use it.

WPA capable wireless cards either usb or PCMCIA/Cardbus  aren't that expensive - better to invest a little cash for the better security.

George

---

### Post by Zzl1xndd on 2007-05-30
> **george29 said:**
> the reason people use encryption algorithms is stop people getting hold of information that they shouldn't - using WEP is not a good solution... if someone decides to, they could grab all sorts of information from the communication between router and wireless computer, e.g. passwords, banking details etc. 

people have wifi as it allows them to be free from wires - if everytime you want to do something like online banking you have to plug in a wired connection, you lose all the benefits of wifi and might as well not use it.

WPA capable wireless cards either usb or PCMCIA/Cardbus  aren't that expensive - better to invest a little cash for the better security.

George

Gotta agree WEP is not the way to go to protect yourself granted it is better then nothing but it takes all of 5 mins to break. I for one live in a apartment building and WEP would never suit what i was gonna do. Just to add something if you are ever on a wireless network that uses WEP or no Encryption at all doing things like banking and such are not safe unless you have logged in to a VPN.

---

### Post by Inxsible on 2007-05-30
I had a Cisco Aironet Card on my T40, and trust me ... IT SUCKED !!!
 
I am so glad IBM stopped using Cisco cards in their machines. I now have a T42 and am quite happy with the Intel 3945ABG PRO/Set :)

---

