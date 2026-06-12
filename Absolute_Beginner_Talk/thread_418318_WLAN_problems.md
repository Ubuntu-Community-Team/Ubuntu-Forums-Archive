---
title: "WLAN problems"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by surfwizz on 2007-04-22
I have an HP laptop with a Broadcom 802.11 b/g WLAN and I am trying out 7.04 on the live CD.  The OS is not recognizing my wireless card.  How do I get it to recognize it?

---

### Post by Pobega on 2007-04-22
Are you sure the OS is not recognizing the card? I thought that Feisty had support for cards like this "Out of the box".

Have you done "iwconfig" or "ifconfig" to see what's going on? How about "lspci | grep Network"?

---

### Post by surfwizz on 2007-04-22
In the dropdown menu for wifi it shows that it logged the SSID and the password, but it shows no signal, even though Windows gets signal from the same spot.

---

### Post by Pobega on 2007-04-22
What drop down menu, network-manager-gnome?

That sounds a little bit weird.

Try this command:

iwlist eth2 scan

And tell me what it comes up with.

---

### Post by fjodork on 2007-04-25
Hi.

I have a similar problem.

I have a 3COM pci prism2 or 2.5 chipset wifi card. I think its detected and all that cause when I press the network manager dropdown menu i can see the networks in range. But when I press the one i want, the network manager icon changes to two blue lines spinning while attempting to connect to the AP, but after a minute or two it goes back to same unconnected state. 

also tryed to connect to a network with WEP encryption and after i dial in the password it shows that its connected, but im still offline and the connection information still shows 0.0.0.0 on ip and everything else.

same card works perfectly in windows and in sled 10.

im very new to linux, so some help would be great.

Since this is a card that i usually dont use(not even in windows) i only need it to work temporarly untill i get my USB wifi stick to work with ndiswrapper. but it does not seem to be on the 7.04 cd and without a network connection i cant download it..

thx in advance

---

### Post by fjodork on 2007-04-26
bump!

---

