---
title: "Making Wireless Work In Ubuntu"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by mmmkile on 2007-05-29
I need help getting connected to my wireless network using Ubuntu 7.04. I have entered my network name, my password and other needed information. Ubuntu can not still find my network.

I am using a wireless card to connect to my network. I am not sure what the wireless card is that i am using. I know that the router is a Linksys WRT54GS.

---

### Post by mkoehler on 2007-05-29
What type of wireless card do you have in your computer? - If you go to System>Hardware Information, you should be able to find out the make and model.  If you provide us with that, we can help you more.

---

### Post by st33med on 2007-05-29
Please post the results from this code in the terminal:
```
lspci
```
This will help us determine the card.

---

### Post by Kobalt on 2007-05-29
The wireless card model would actually be useful...

---

### Post by mmmkile on 2007-05-29
I know it is a Linksys brand card.

---

### Post by Eagle 101 on 2007-05-29
To help you find out what card you have, just copy paste the output of lspci. To do this open up the terminal and put 'lspci' in it. Then copy paste the output here.

---

### Post by Kobalt on 2007-05-29
Is it an USB or a PCMCIA card ?

---

### Post by mmmkile on 2007-05-29
Thanks.
i will have to boot back into ubuntu first
thanks again

---

### Post by mmmkile on 2007-05-29
Pcmcia

---

### Post by Kobalt on 2007-05-29
It should be written on your card which model it is... Otherwise plug it in and run lscpi, you should find it in the list.

---

### Post by mmmkile on 2007-05-29
WMP54GS
Wireless-G PCI Adapter with SpeedBooster.
This is the type of card. I am 100% sure.

---

### Post by holihue on 2007-05-29
You can try [ndiswrapper.]("http://ndiswrapper.sourceforge.net/joomla/")


It is a program that run windows driver for networking.

---

### Post by mmmkile on 2007-05-29
Ok. So I install it in Ubuntu or Windows?

---

### Post by holihue on 2007-05-29
I downloaded a .zip file for my intel wireless.

---

### Post by .:Black:. on 2007-06-04
Hello all.....I stumbled on this thread because I am having the exact same problem as mmmkile.  I also have a WRT54GS router and the network card is WMP54GS.  Here is a screenshot of the type of PCI card I have:

[IMG]http://img368.imageshack.us/img368/2579/screenshotdevicemanagerpt3.png[/IMG]

Can someone explain what ndswrapper is and how it might help me?  I downloaded it and extracted it, but I have no idea what to do now.  I may need stuff described to me step by step, because I've only been using Linux for half a day (I got hold of a spare computer and decided to get the ball rolling with my eventual separation from Microsoft).

I read somewhere that Ubuntu may not support my wireless card.  I thought I would check with the source here at the Ubuntu forums. 

Thanks!

---

### Post by Papi-KB7VGW on 2007-06-04
try this link.  Itis a how to from this forum

[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)

---

### Post by .:Black:. on 2007-06-06
Thanks, I actually got it working pretty easily by installing the following package:

bcm43xx_compwiz18.1-all.deb.

---

