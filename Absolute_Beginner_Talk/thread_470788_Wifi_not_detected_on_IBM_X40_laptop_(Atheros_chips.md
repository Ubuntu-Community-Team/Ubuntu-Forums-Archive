---
title: "Wifi not detected on IBM X40 laptop (Atheros chipset)."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2007-06-11
Help please!
I am having a frustrating time enabling my wifi on my X40 notebook. I loaded on 6.10 and then downloaded by wire approx 169 update packages(!) including the linux restricted packages that contain the madwifi drivers, which I understand are relevant to this chipset, I was unable to detect in Synaptic "madwifi tools" to install, although they all have green boxes, so I know they have been downloaded and are there somewhere and need to be identified to be installed(?) Accordingly I am still unable to turn on the wifi. This is the detail I get when ifconfig is typed in terminal, (which does not come as a surprise):-

=================================

lo no wireless extensions.

irda0 no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"Linksys"
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:17 dBm Sensitivity=0/3
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=0/94 Signal level=-95 dBm Noise level=-95 dBm
Rx invalid nwid:73 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

=============================

Any help would be greatly appreciated. Thanks.

---

### Post by crispy_420 on 2007-06-11
First of all, why are you still using 6.10? Nothing against 6.10 but it is not a LTS edition. Next are you using network-manager to connect? I also have a atheros based chipset and it has had no issues, other than the fact that they are none to be slow to connect. If you are using network-manager to connect, I once read that it does not like to connect to a generic named network (eg. Linksys) due to security concerns. Also what security settings are you using? Did you install WPA support? Atleast you can see the network.

---

### Post by Hookheathen on 2007-06-12
Thanks for your reply.
I use 6.10 first off since that is the CD version I have. (On my Fujitsu I originally loaded this and then upgraded). I am repeating the same installation method on the IBM. 

To attempt to connect I go into System - Admin - Network Settings - Wireless connection to check on the settings. I have not loaded WPA support on this laptop but I use wifiradar on the Fujitsu. 

I believe it is a problem with association. The driver is there but it is not connecting up. Does this help?

---

### Post by crispy_420 on 2007-06-13
Download Feisty and use that for install. I have done it with two laptops (Averatec w/ atheros & Acer w/ intel) and I had no wireless issues at all. Atheros worked right away with no driver install and was installing updates wirelessly in minutes after install.

---

### Post by Hookheathen on 2007-06-15
Thank you Crispy, will give it the old school try and let you know how I get on. 

Am I right in thinking I just boot up from the downloaded Feisty CD and it will automatically identify an earlier version already loaded and will update only the packages needed, or, horrors of horrors, would it load on a second version?

Thanks, Hookheathen

---

### Post by nickpaton on 2007-06-21
If you install a new Feisty over Edgy, Feisty will install over Edgy effectively getting rid of all of Edgy in the process.
So if you have any important docs etc make sure you save them onto a CD or whatever first.

I've PM'd you M8, but will continue to monitor this post.

---

### Post by lazyart on 2007-06-21
> **Hookheathen said:**
> Am I right in thinking I just boot up from the downloaded Feisty CD and it will automatically identify an earlier version already loaded and will update only the packages needed, or, horrors of horrors, would it load on a second version?


The update manager should let you upgrade to Feisty while keeping your setup. Some say that's a accident waiting to happen, however I went from Dapper->Edgy->Feisty that way with no problems.

---

### Post by crispy_420 on 2007-06-21
lazyart some have not been so lucky with upgrades

---

