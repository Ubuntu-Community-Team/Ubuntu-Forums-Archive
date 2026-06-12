---
title: "i know Ive asked, but please help"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-02-23
I have tried every way I know, i have read just about every thread, and have pulled out just about every hair. Please help me get connected to the network.

Ive tried wifi (what i really need) and Ive tried wired ( just to see if i can make some head way) and cant get connected.

Ive tried 4 different wifi cards, and two different pcmcia ethernet cards, replaced my wifi router... and still no luck. I have also installed gtkwifi and wifi radar and both see networks but will not connect.

would somebody please sugest what I could do to get me connected.

---

### Post by taurus on 2006-02-23
The first thing you need to do is to list the brand names and models of those cards so if people have it working, they will tell you exactly how to set it up...  Otherwise, it's kind of hard to tell you if we don't know which ones you have.

---

### Post by chrluc on 2006-02-23
well i have a trendnet tew-226pc (well actually i have 26, for 26 different laptops and all have to get access to the network. i could sell the and get a different card but i would prefer to get these working) and i have got the ndis wrapper and it seems to be working and i can activate in "networking" and device is present.

the router in a linksys g router ( and I believe it is in DHCP mode)

---

### Post by chrluc on 2006-02-23
i cant seem to get the wired network working either. Im sure there is a setting that would effect both the wired and the wifi. but i cant seem to find the common thread.

any ideas?

---

### Post by Iowan on 2006-02-23
I had a reply almost ready to hit the [SUBMIT] button, but since I know almost nothing about wifi, I was afraid the info would be next to useless.  Where do "we" stand with the wired cards?  I don't know if wifi uses IP addresses, but wired does.  Does **ipconfig** show your card(s) with an address and subnet mask?  Can you ping your router?  Are you connected to the router with the proper cable (straight vs crossover)?

---

### Post by chrluc on 2006-02-23
thanks for your reply first off, any guideance helps! when i do ifconfig it show the inet addr:192.168.0.102 Bcast:192.168.0.255 Mask: 255.255.255.0
UP BROADCAST RUNNING MULITCAST MTU:1500 Scope:link

then everything else is 0


does that help?

---

### Post by nalmeth on 2006-02-23
in SETTINGS --> ADMINISTRATION --> NETWORKING is your eth0 set for dhcp? Same for your wireless.

Can you boot up with the liveCD to see if you get internet? Did you not have internet when you installed?

You should find some answers at these links:
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

