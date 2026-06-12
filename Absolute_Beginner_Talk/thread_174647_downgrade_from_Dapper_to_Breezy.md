---
title: "downgrade from Dapper to Breezy?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-05-12
Hi,
I had a troublesome box that refused to install Breezy from a CD.  I managed to get Dapper to install (plus temporarily filled it up with extra memory!)

However I can'te get my wireless USB to work in Dapper, it just freezes up.  Does anyone know if I can Downgrade from Dapper to Breezy, without reinstalling from CD/DVD?

Cheers

---

### Post by Kobalt on 2006-05-12
Actually no, you can't downgrade... But we can help you fix your USB wirless problem ;) What's your USB wifi key model ?

---

### Post by damianubuntu on 2006-05-12
Hi Kobalt,
I originally posted the wireless problem here:

[http://www.ubuntuforums.org/showthread.php?t=174025](http://www.ubuntuforums.org/showthread.php?t=174025)

before thinking that maybe I should just downgrade!

Cheers for any advice.

---

### Post by Kobalt on 2006-05-12
I read your thread, but I'll be answering on this one, if you don't mind. 
It's quite wierd, becuasue lynksys cards are usually working quite well on Ubuntu and yours (with a rt2x00 chipset) should be working well...
Step by step then. :) 

Check if you have a wireless extension detected with this and get your interface (eth0, wlan0, etc...) 
```
$ iwconfig
```

Then activate your wireless interface and see what's happening : 
```
$ sudo ifup <interface>
```

If you get an IP, it should be working then, if not, we'll have to figure out a way using ndiswrapper...

---

### Post by damianubuntu on 2006-05-12
iwconfig gives me rausb0.

However I can't do ifup rausb0 because as soon as I activate from System,Networking the whole of Dapper freezes and all I can do is power down and reboot, at which point the device is still unactivated and uncofigured!

---

### Post by Kobalt on 2006-05-12
And have you tried pluging it before booting your computer ? 
Also, did you check on Launchpad if this is a known bug from dapper ?

---

### Post by damianubuntu on 2006-05-12
ITS WORKING NOW!

What a strange fix! Just in case it gave more information, I tried to config the adaptor in networking, but NOT activate it, just OK and close.  Rebooted, and then tried to activate, and everything is OK! 

Ubuntu is great again!

Thanks for your help Kobalt, sorry to waste your time!

---

### Post by Kobalt on 2006-05-12
You didn't waste my time at all, I'm glad to help. And I have bought a Lynksys PCMCIA card and modem/routeur, so I was kinda helping myself as well :p 
Enjoy your WiFi damianubuntu !

---

