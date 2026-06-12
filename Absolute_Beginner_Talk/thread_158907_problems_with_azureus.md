---
title: "problems with azureus"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-11
hi all, i have installed azureus on my ubuntu laptop but i can't get any of the ports from 6881-6889 to work when i run the test.  I am using a D-Link wireless router to connect to the cable internet.  What should I do?  At the bottom of Azureus there are three colored circles.

1. green - Ratio
2. red - Firewalled
3. yellow - DHT firewalled

As far as I know, i am not running any firewall with ubuntu.  Any suggestions on getting around this would be greatly appreciated

---

### Post by taurus on 2006-04-11
You need to go into your router and open up those ports!!!  The problem is not your Ubuntu but it's your router that blocks those ports...  So, look at the doc that comes with your router on how to access and change port with it.

---

### Post by trent dillman on 2006-04-11
Also, install Firestarter and open the ports with that (in case iptables is to blame).

---

### Post by WelterPelter on 2006-04-11
Often you can configure the router in a web browser, by using this link: [http://192.168.1.1](http://192.168.1.1)

It won't work for all of them, but it's worth a shot.

---

### Post by sublime on 2006-04-12
portforward.com

best port forwarding tutorial on the web

---

### Post by racermike1967 on 2006-04-12
I tried to do the port forwarding with the exception of maintaining a static ip address.  Reason I did not do this is because I move my laptop around a lot and would require the use of DHCP.  After finishing the port forwarding, I have not reset my router or my computer so my IP address should be the same.  However, my azureus is still not functioning properly.  At the bottom, there are three circles with the following colors:
1. green - ratio
2. green - NAT
3. yellow - DHT Firewalled

What can I do to fix this problem?  I get green cirlces next to my torrent files but the download speed is still 0 B/s for all three of my torrent files.  Am I not understanding something here?  At the bottom right corner there are two numbers displayed, download rate and upload rate.  I have set both at unlimited but my upload rate goes as high as 78 B/s and my download rate is no more than 6 B/s.  Can anyone help me?

---

