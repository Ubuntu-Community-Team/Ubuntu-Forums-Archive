---
title: "DHCP help"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by rzapeople on 2006-03-25
I know this was prolly posted in some thread and solutions were posted, but I done spent the last two days looking for a thread that with a solution. 

Okay, my problems are as follows: 
1. I installed kubuntu, got ubuntu instead... 
2. During initial setup DHCP was never configured properly and I keep gettin [fail] every time a process tries to attempt to configure DHCP
3. I cant browse the web. All I can acces is ubuntu.com and related sites, all others are not accessible except for a few, which really puzzles me. I can access [www.mmegi.bw](www.mmegi.bw), [www.arizona.edu](www.arizona.edu) for example (including these forums and ubuntu related sites. But I cant get to [www.yahoo.com](www.yahoo.com), [www.google.com](www.google.com) nor any other site. 

So I am truly stumped. If anyone got tests I can run please post and please keep in mind I am a newbie when it comes to linux. Everything is a mystery and I am now tired of playing sherlock holmes with this internet thing... please help.....

R

---

### Post by Kurt` on 2006-03-25
Can you try this? Go to a machine that has working internet access (windows/linux) and write down the following information:

the IP (probably 192.168.x.y)
the subnet mask
and the default gateway/gateway address
the DNS servers

Then, inside Ubuntu, go to System->Administration->Networking. Select (assuming you're using wired here) "Ethernet connection" and hit properties. Select "static IP address" from the drop down box next to Configuration. Then enter the values you wrote down above. Then activate/reactivate the connection.

Then, still in the Network page, click the DNS tab and see if the correct servers are being set.

At this point, assuming the DNS servers are being discovered correctly, your internet should work fine... then someone with more knowledge of Ubuntu can help you with the DHCP problem. :)

---

### Post by ubuntuuser on 2006-03-26
Please provide the output of ```
ifconfig
``` and ```
sudo dhclient eth0
``` Be sure to replace eth0 with the correct interface if you are using a different one (like wlan0, ath0, eth1 etc.). If you are using WIFI, also add the output of ```
iwconfig
```
Any additional information, such as your network setup and your type of internet connection (DSL, dial-up ...) would be helpful.

---

