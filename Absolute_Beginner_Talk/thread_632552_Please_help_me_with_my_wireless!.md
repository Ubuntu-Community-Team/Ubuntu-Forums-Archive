---
title: "Please help me with my wireless!"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by agentaaron on 2007-12-05
I am using Ubuntu 7.10 on a HP nx9010 with the standard Broadcom 43xx wireless chipset. Though this version of Ubuntu is able to find the card and allow me wireless access, it is sometimes painfully slow. 

I read through these forums and have a ton of them bookmarked and tried everything about disabling ipv6 in firefox and in the terminal...neither have worked.

Just for an example, I was going to speedtest.net and was getting a result of 285kp/s download and 102kp/s upload and a ping of 314ms. I then disconnected the wifi and ran the  cable directly from the modem to my pc and saw much better results 8426kb/s download and 1850kb/s upload with a 81ms ping. 

also, when im wireless and I right click on the network connection meter at the top right and go to connection information it says its only connecting at 24mb/s where as when im plugged in I get 100mb/s.

I am in need of help to get my wireless up to speed for streaming and torrent downloads. I have a bit of knowledge of computers but am brand new to the Linux world...so some dumbed down instructions would be very helpful. Thanks guys.

---

### Post by jasmuz on 2007-12-05
You shouldnt compare cabled versus wireless internet access.
Remember that obstacles as walls and such, lower your signal strengh and your ping times and speed vary over the air.

---

### Post by agentaaron on 2007-12-05
Yeah, I am aware of the obstacles that can make a difference in performance, but would you not agree that 285kp/s is a very low number for download rate?

In both cases I had the computer less than 36 inches from the router and modem as I only have a very short Ethernet cable.

---

### Post by jasmuz on 2007-12-05
I must say, that you TRULY have an issue there.

Are you using your Wireless via NDISwrapper? If so, there might be a performace issue.

---

### Post by agentaaron on 2007-12-06
No im not using NDISwrapper, When I installed the OS, the restricted driver manager installed the driver for me and I left it at that. 

I dont mind trying to use NDISwrapper, I downloaded it but unfortunately im not to sure where to pull the driver from.

---

### Post by jasmuz on 2007-12-06
Using Ndiswrapper you will be loading the Windows driver via a wrapper.
So, you should download such driver from the manufacturer.

Im sorry to say this, but you will get better support on the native linux drivers than Ndis based ones.

---

### Post by edm1 on 2007-12-06
Unfortunately broadcom do not write drivers for linux. The drivers installed have been reversed engineered so you shouldnt been suprised if the wireless card is not working 100%. If you are desperate for full speed wireless all i can recommend is buying a [supported card]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

---

