---
title: "How can I determine my router's IP address?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-07
I am trying to access my wireless router, but I cannot determine my IP adress.

The model of my wireless lan is Linksys Wireless-G Access point WAP54G. I suppose that the default IP address is 192.168.1.1, but I cannot go to that URL. 

I remember changing that IP address, but I forgot what IP address I assigned so I pressed the restart button on the router, but I still cannot access it using 192.168.1.1.

How can I determine my router's IP address?

---

### Post by bigken on 2007-04-07
try this command in a terminal [B]sudo dhclient (name of card ie eth0)
[/B]

---

### Post by freebird54 on 2007-04-07
Apart from guesswork - or going to the web site of the manufacturer and hoping its on a FAQ somewhere there all I can think of is:

1.  Fire up a browser, and try 192.168.1. 1-255  (choosing most likely ones first like 100 and 200 and 255)

2. trying to ping the same way - and look for the one that answers!

Bit of a time waster - but there it is.  I do KNOW that a restart or power out will not change it, but there might be a reset button that, if held long enough, will restore defaults...

Just wondering - why change it?  It is behind the NAT wall, and you *DO* have a strong password on it, right?  :)

EDIT:  see above first - hadn't thought of that :)

---

### Post by OffHand on 2007-04-07
No need to start two threads for your issue. Therefor I will answer in your first thread.

---

