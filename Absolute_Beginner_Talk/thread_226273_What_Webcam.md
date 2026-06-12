---
title: "What Webcam?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by veelivar on 2006-07-31
Hello,

I'm looking at getting a web cam for my computer.  Having being burnt before when I have bought hardware and then found it didn't work on ubuntu I thought I would ask here to see what webcams you have and how well they work.

So whats good and what's not? :) 

Do you know any software for linux a that acts like a security center so you can mail clips on motion etc?

Also is it possible to set it up so that you can log in remotly to a live feed from the webcam?

Cheers,
Dan.

---

### Post by Dinerty on 2006-07-31
I use this webcam on Ubuntu [http://www.labtec.com/index.cfm/gear/details/EUR/EN,crid=30,contentid=731](http://www.labtec.com/index.cfm/gear/details/EUR/EN,crid=30,contentid=731)

Plug it in and worked immediately, no extra install needed !

---

### Post by veelivar on 2006-07-31
Thanks for gettign back to me.  I've just done a quick search to get rough prices and I can't find any where (in english) that sells it :(

It seems that every webcam I have found on a store has some problems or an other on Linux.  

Having said that i have found some cool software here [http://www.zoneminder.com/](http://www.zoneminder.com/)

just need to find a camera now! :(

---

### Post by Dinerty on 2006-08-01
I got mine from argos, however I just checked their website and they dont seem to have my model in, if your from uk, go into your local argos and take a look through their book, it should be in there

Nice software there :)

---

### Post by loell on 2006-08-01
almost if not all logitech webcam can be detected in ubuntu

---

### Post by Cariboo1938 on 2006-11-14
> **loell said:**
> almost if not all logitech webcam can be detected in ubuntuIt seem's so... it detected mine > karibu@BitByter:~$ lsusb
Bus 003 Device 002: ID 07cc:0301 Carry Computer Eng., 
Co., Ltd 6-in-1 Card Reader
[COLOR="DarkOrchid"]Bus 002 Device 002: ID 046d:08da Logitech, Inc.[/COLOR] 
Bus 001 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
karibu@BitByter:~$ Don't I need to install a driver now?
Where do I get the right driver?

---

### Post by loell on 2006-11-14
> **Cariboo1938 said:**
> It seem's so... it detected mine Don't I need to install a driver now?
Where do I get the right driver?

that's it, you can use it now :KS 
judging from the product id and vendor id
0x046d 	0x08da
its a logitech quickcam messenger

run an application that uses a webcam, and poof :D

---

### Post by Cariboo1938 on 2006-11-14
> **loell said:**
> that's it, you can use it now :KS 
judging from the product id and vendor id
0x046d 	0x08da
its a logitech quickcam messenger
run an application that uses a webcam, and poof :DI'm in a hurry! I'll try it tomorrow morning. BTW how do you read the detected line?

---

### Post by loell on 2006-11-15
Bus 002 Device 002: ID 046d:08da Logitech, Inc. 
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")
these are the webcams for spca5xx drivers which is included in ubuntu

---

### Post by Cariboo1938 on 2006-12-06
> **loell said:**
> Bus 002 Device 002: ID 046d:08da Logitech, Inc.[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")
these are the webcams for spca5xx drivers which is included in ubuntuThank you, loell, for your very informative and detailed replies. I was away for a while and I couldn't find an application yet using a web-cam, so I actually didn't check yet. I have to postbone the project until I know where to use the web-cam

---

