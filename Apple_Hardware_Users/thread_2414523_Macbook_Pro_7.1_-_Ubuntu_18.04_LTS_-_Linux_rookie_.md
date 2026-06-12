---
title: "Macbook Pro 7.1 - Ubuntu 18.04 LTS - Linux rookie - Cant get wifi to work"
date: 2019-03-11
forum: Apple Hardware Users
---

### Post by marcusmedgyesi on 2019-03-11
Laptop: Macbook Pro 7.1 (bought in European market) On Ubuntu 18.04 upgraded from 14.04 - 16.04 - 18.04 

Wifi persistently does not work. 

There is no option for Broadcom STA driver in "additional drivers" section.

Have done some cycling through Wifi drivers and blacklisting to no avail. 
Possible I might have misses a combination that works. Can't be sure.

As suggested on other similar topics I have run "**Wireless script**" from signature of [**[COLOR=#C61919][B]wildmanne39**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=508533").
output is: [http://paste.ubuntu.com/p/2kRrwjy7Hp/](http://paste.ubuntu.com/p/2kRrwjy7Hp/)

No idea if it helps. (as I am for the most part a newbie) but:
Only connectivity related item result via "lspci"is: 
03:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)

"sudo dmidecode" paste here if it helps: [https://paste.ubuntu.com/p/CZDZvfc2j9/](https://paste.ubuntu.com/p/CZDZvfc2j9/)

I am connected to the internet this instance on the laptop via USB tethering from a phone.
I can also confirm that Bluetooth tethering also works <- not sure if that helps...

and "rfkill list" shows nothing blocked.

I would appreciate some help getting wifi to work. 
Thanks

(My first post here ever. if I did something wrong/"break guideline" notify me and I will correct it to the best of my ability)

---

### Post by wildmanne39 on 2019-03-11
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by wildmanne39 on 2019-03-11
Right now I am not able to help much but I can tell you that your wifi device is not listed so your card probably stopped working, you can try to clean the contacts and reset it, I know this is hard to do on a laptop, even if the driver is not listed or more then one is listed your card should still show up.

---

### Post by marcusmedgyesi on 2019-03-12
Hey thanks for the insight. I mistook my ethernet card for a wifi card. *facepalm* 

After looking into the difficulties of reseating the wifi card on Macbook pro 7.1 I have decided to go with a wifi dongle instead.

But thanks again for the help.

---

