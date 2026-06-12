---
title: "Asus A6K Laptop Wireless Network"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by SprEA on 2006-02-20
Hey,
I just installed Ubuntu and I need to get on the local wireless network.

I've been looking abit around the forum and I've tested out ndiswrapper. But I can't seem to find a driver that work.

Anyone have the same laptop and know where I can find the driver that work with ndiswrapper?

Thanks in advance.

---

### Post by scenestar on 2006-03-11
I've been having the same problem on my asus z92k (basicly an a6k but without the webcam). 

I'll post a howto as soon as I get it to work.

---

### Post by [h2o] on 2006-03-24
I installed Dapper Drake on my Asus A6 and wireless networking was detected at install time. Might be a different network card though.

---

### Post by PartisanEntity on 2006-11-10
Hi, I too just installed Ubuntu 6.10 on my Asus A6, and I am clueless as to how to proceed to access the net using my wireless card. Its an Asus card with Broadcom drivers I think. (wl-120g)

---

### Post by nbk on 2006-11-23
Im bringing the subject back, because I'm having the same problem. I have ubuntu 6.06 LTS & ASUS A6KM. If someone succeded it meanwhile please let us know or mail me the link of the drivers at [email]andrejsok@gmail.com[/email]
thanx

---

### Post by PartisanEntity on 2006-11-24
I managed to get wifi working, also with wpa encryption on my Asus A6K with Ubuntu 6.06.

My experiences:

Fresh install of Dapper
First connect through ethernet to get the latest updates
While still connected try these two tutorials (they worked for me):
(assuming you have a broadcom wifi card): [http://www.ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom+4306+With+Ndiswrapper+54+Mbps](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom+4306+With+Ndiswrapper+54+Mbps)
then this:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Tip: for the 2nd tutorial (it may be obvious to long time Ubuntu users) once you have installed Network Manager you need to unplug your ethernet cable, only then will Network Manager show you wifi networks.

Good luck :)

---

### Post by berbu on 2007-04-20
Hi,
I've got an ASUS Z9200U laptop running Ubuntu and i also have some trouble getting that wifi card to work.
Via the lshw command I checked that the card is recognized and associated to a driver, but it is marked as DISABLED.
The WifiDocs/WirelessTroubleshootingGuide mentions the following:

[COLOR="Blue"]      Newer laptops come with features to disable the wireless radio to save battery when not in use. Usually this is switched by a FN+Fx key combo or specific button for the purpose. It is possible driver and everything is ok but the wireless device is in the disabled state and can't be used. Using the designated key(s) in linux sometimes does not work.

      Usually this is apparent by running the lshw command you see *-network:1 DISABLED or if you run the iwconfig command you see eth1      NOT READY!.

      So how do you rectify this? It varies so much the exact solution can't be put here in this document for all the different models. So...

   1.

      Look at the LaptopTestingTeam page here on the wiki to see if your laptop is listed with any information.
   2.

      Do a google search using terms such as manufacture, model, linux, wireless, enable, button, radio....etc. When searching and finding similar pages that don't help, use words that are used in those pages to help you search.
   3.

      Go to the [WWW] ubuntu forums and ask, maybe someone else has the same laptop and knows the work around.[/COLOR]

The Fn+F2 combination doesn't seem to work for my PC, so I'm getting to step 3 and ask around on a forum. Anyone an idea on how to enable the wireless network card on ASUS laptops?

Thanks

---

### Post by berbu on 2007-04-21
OK, problem solved.
It had nothing to do with the laptop activation key after all. It just seems the bcm43xx driver is not working for bcm4318 cards. I solved the problem with ndiswrapperthanks to a nice post on
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

