---
title: "Network Shareing"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by Hamad on 2005-06-14
I have two computers, one is Ubuntu, and the other is Windows XP Professional. Ubuntu has an internet connection, and i want to share my connection with the computer with Windows XP on.
The internet connection device is Lucent CellPipe USB-20A.
Each computer has a network card that is D-Link-G122. I had to get ndiswrapper to allow it to work on Ubuntu. The Access Point is Linksys wireless-g ADSL Gateway.
I want to know how to share the internet connection on Ubuntu with Windows XP. Can anyone help ?

---

### Post by Jussi Kukkonen on 2005-06-14
[QUOTE=Hamad]I have two computers, one is Ubuntu, and the other is Windows XP Professional. Ubuntu has an internet connection, and i want to share my connection with the computer with Windows XP on.
The internet connection device is Lucent CellPipe USB-20A.
Each computer has a network card that is D-Link-G122. I had to get ndiswrapper to allow it to work on Ubuntu. The Access Point is Linksys wireless-g ADSL Gateway.
I want to know how to share the internet connection on Ubuntu with Windows XP. Can anyone help ?[/QUOTE]

Normally you'd just connect to your wireless access point from both computers. No 'sharing' as such needed, your router will take care of that. If you want more help, I think you need to tell us a little more about your network setup.

Your Linksys is a [WAG54g](http://www.linksys.com/international/product.asp?coid=6&ipid=371)  or something like it, right? It has an ADSL modem, router and a wireless accesspoint.  That's pretty much everything you need... what do you need the Lucent ADSL modem for? How exactly do you have them connected?

Do you have any connection on either machine at the moment? wireless or not? Do you know if you are using dhcp (from your ISP and/or from your router)?

---

### Post by Hamad on 2005-06-14
[QUOTE=Jussi Kukkonen]Normally you'd just connect to your wireless access point from both computers. No 'sharing' as such needed, your router will take care of that. If you want more help, I think you need to tell us a little more about your network setup.

Your Linksys is a [WAG54g](http://www.linksys.com/international/product.asp?coid=6&ipid=371)  or something like it, right? It has an ADSL modem, router and a wireless accesspoint.  That's pretty much everything you need... what do you need the Lucent ADSL modem for? How exactly do you have them connected?

Do you have any connection on either machine at the moment? wireless or not? Do you know if you are using dhcp (from your ISP and/or from your router)?[/QUOTE]
Each PC has a D-Link-G122, and the Linksys is the access point (Havn't used the ADSL modem in it), and i have one computer witch has Ubuntu installed and has an internet connect, while the other one doesnt, so i want to share my internet connection with the other pc. I don't think i'm using dhcp (im not sure)

---

### Post by Jussi Kukkonen on 2005-06-14
[QUOTE=Hamad]Each PC has a D-Link-G122, and the Linksys is the access point (Havn't used the ADSL modem in it), and i have one computer witch has Ubuntu installed and has an internet connect, while the other one doesnt, so i want to share my internet connection with the other pc. I don't think i'm using dhcp (im not sure)[/QUOTE]
So I'm guessing your setup is this:
[INDENT]*internet <--> Lucent cellpipe <--(USB)--> Ubuntu machine*
You're not using the wireless devices yet, but you'd like to connect your windows machine somehow too?[/INDENT]

(The rest assumes I guessed correctly. Disregard if I didn't)
If you want to keep using the Lucent Cellpipe, I can't help you: I have no idea how to connect a usb-modem and a wireless access point. See, normally they're just plugged in one after one, like this:
*internet <--> modem <--> router/access point <--> all your machines*.
The usb connection makes it a little difficult.

My advice: ditch the Lucent and plug your Linksys in its place. You might have to connect one of your machines to the linksys with a network cable for the first time (to set it up via the web interface). Can't help you with that very much, it's been a long time since I used a Linksys router/AP. Someone else in the forum will probably help you though (of course you'll need an internet connection for that... tricky these network problems).

---

