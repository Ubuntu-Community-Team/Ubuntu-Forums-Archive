---
title: "Connecting to internet :P"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by frosty36 on 2006-01-27
Woah I have searched and searched read and read and I can't find where it tells you TO CONNECT TO THE INTERNET!!!

My modem and all is plugged in ... do I need to install the drivers or somthing?
(I'm askling and not doing because I'm at my computer btw :p)

---

### Post by kvorion on 2006-01-27
Please mention what kind of a connection is it that you have.

---

### Post by frosty36 on 2006-01-27
dsl / adsl (well dial up , but broadband dial up :p)

---

### Post by frosty36 on 2006-01-27
My modem is a sagem f@st 800 E2T

Please help me :'(

---

### Post by bscbrit on 2006-01-27
[http://ubuntuforums.org/showthread.php?t=45974](http://ubuntuforums.org/showthread.php?t=45974)

Try this link from 3 weeks ago - a search is all it took:-D

---

### Post by kvorion on 2006-02-01
[QUOTE=frosty36]dsl / adsl (well dial up , but broadband dial up :p)[/QUOTE]

Sorry to come back to it so late. Well I use a connection similar to the one you mentioned. You can do this. Go to google and search for "Roaring Penguin pppoe client" better known as rp-pppoe. Download the souce and install it on ur box. Follow the instructions given in the ReadMe file and it should work perfectly. One problem I faced was that it requires a different version of gcc than the one that comes installed on Ubuntu by default. 

Just try installing it as is......and if it does work then fine. Else you will have to install the older version of gcc, make that your default compiler and compile again. I can help you with that too if u need

---

### Post by frosty36 on 2006-02-02
OK ... I downloaded the .tar.gz file; as I'm just trying with the boot CD I was wondering if there was somewhere on there I can /  should put it ... or do I install it on Windows :confused: (I guess not ...)


I don't know if this will help anyone help me ... but ...

USB ADSL WAN Adapter - Device Name
isdn - Device Type
PPP - Server Type
TCP/IP - Transports
MD5 CHAP - Authentication

---

### Post by kvorion on 2006-02-02
[QUOTE=frosty36]OK ... I downloaded the .tar.gz file; as I'm just trying with the boot CD I was wondering if there was somewhere on there I can /  should put it ... or do I install it on Windows :confused: (I guess not ...)


I don't know if this will help anyone help me ... but ...

USB ADSL WAN Adapter - Device Name
isdn - Device Type
PPP - Server Type
TCP/IP - Transports
MD5 CHAP - Authentication[/QUOTE]

If you have downloaded the .tar.gz file then go ahead extract it and type ./go
If things go well then it should get installed. No I dont think you will find this on the cd.

---

### Post by frosty36 on 2006-02-02
Well I boot from a live CD ... I'm on Windows right now ... so I must have to put the file somewhere ... (so I just type /go in the terminal :confused:)

---

