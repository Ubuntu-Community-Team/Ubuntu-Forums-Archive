---
title: "Unable to connect to the Internet"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-06-16
Hai Everyone, I am a new user of ubuntu and I tried to connect to the internet using GNOME PPP.I have a dialup connection to the internet using a krypton 56K modem. The dialer was good but there was an error message saying " Cannot Detect Modem".It displayed,



 WvDial: Internet dialer version 1.56
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Someone help me please. 


Thanks in advance:-)

Rabindranath.

---

### Post by meborc on 2007-06-16
ahh... can't help you much... try this - [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Rabindranath on 2007-06-16
when I do what you say,it says "Scanning Modem" and it says " No connections found". When I use GNOME PPP it is unable to detect my modem. Do you know what properties to enter in GNOME PPP.in the 'modem' tab?
Is there any other way to connect to the internet using a dialup connection? 
Please help me ....

---

### Post by Shazaam on 2007-06-16
Lets get some information first. Is your modem made by this company?  [http://www.priyagroup.com/ithome/index.shtml](http://www.priyagroup.com/ithome/index.shtml)

And if it is what is the model number?

---

### Post by Rabindranath on 2007-06-16
Yes, that is the company alright. The modal number is V.92 56K PCI.

---

### Post by Shazaam on 2007-06-16
No that's the type. Go to this page and find your modem.  [http://www.priyagroup.com/ithome/products/commniproduct.shtml](http://www.priyagroup.com/ithome/products/commniproduct.shtml)

---

### Post by Rabindranath on 2007-06-16
I think the modal number is PS560PCI-F0. But mine is internal and has fax and voice.

---

### Post by Shazaam on 2007-06-16
Ok I have good news and bad news. The good news is you CAN get drivers for this modem to work with Linux.
The bad news is the company that made the chipset for your modem was sold to Conexant. Linux drivers for Conexant winmodems can be found here-- [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)
They have two types. Free at 14.4 or paid at full 56k speed. The paid ones are $20 US.  What you might want to do is find a good EXTERNAL modem for a reasonable price.

---

### Post by Rabindranath on 2007-06-16
Ok, thanks... Ill try that...

---

