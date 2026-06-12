---
title: "56k Modem"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by alsolo on 2005-12-30
Hello everybody
i've just installed Ubuntu on my computer. I'd like to set up internet connection (56k) but i dunno how to do that. I have a serial 56k modem (Topic Modem CTR21 Serial). Please, can you help me? What should i do?
Thanx very much
Silvio

---

### Post by thekiller on 2005-12-30
just plug an ethernet line from your modem to your computer, and then do 

sudo dhclient3 eth0

Everything should work like charm provided your modem works !

EDIT : I assumed you have a DHCP connection

---

### Post by alsolo on 2005-12-30
thanx thekiller but my modem is only SERIAL. It has no ethernet socket, i think it is five years old....

---

### Post by thekiller on 2005-12-30
I have never used serial before, but on searching on wiki i found this howto which might be helpful to you, 

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

---

### Post by alsolo on 2005-12-30
I'll read that!
thanx again you were very helpful
best wishes for the new year
s

---

### Post by buffer_overflow on 2006-08-07
Hello,
i bought the same modem

Trust Computer Topic Modem CTR-21 Serial 56K Modem extern 

at ebay and even for win98/2000 no drivers are available in the web.
Have you found a solution?

buf_over

---

### Post by darrenm on 2006-08-07
the wiki page posted above should be the solution :)

---

### Post by zxee on 2006-08-07
> **buffer_overflow said:**
> Hello,
i bought the same modem

Trust Computer Topic Modem CTR-21 Serial 56K Modem extern 

at ebay and even for win98/2000 no drivers are available in the web.
Have you found a solution?

buf_over

Have you checked at [www.linmodems.org](www.linmodems.org)
You can download the scamodem tool there and see if the chipset the modem uses is supported. 
Dial up modems are getting rarer-in use so it's an art to get them working-sometimes. Most developers are not using them either:( 
For info on how to get a supported modem configured see the link in my sig

---

### Post by The Other Dude on 2006-08-07
Hey, thanks for that link! [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")  I've got a Lucent that is kaputt, I tried using ScanModem but am stuck in the mud for the moment.

---

### Post by zxee on 2006-08-07
> **The Other Dude said:**
> Hey, thanks for that link! [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")  I've got a Lucent that is kaputt, I tried using ScanModem but am stuck in the mud for the moment.

If you want to be more specific about the mud I'll try to help, or go thru the howto as completely as possible being put on notice that dapper IMO & IMExperiance was released with big problems. If dial up continues to be a problem you can either go back to breezy or try edgy. I'm using edgy now and while a few problems are apparent (understandable for a test release) dial up sets up like a charm.i.e you will have to use commandline to connect until you apt-get gnome-ppp-which BTW is broken in dapper.

---

