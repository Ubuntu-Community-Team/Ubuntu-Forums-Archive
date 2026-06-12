---
title: "WIFI issue on Macbook Pro Core 2 Duo (Atheros AR5008)"
date: 2007-05-01
forum: Apple Intel Users
---

### Post by Romu on 2007-05-01
I'm creating the thread to summarize the issues found about the Wifi on the Macbook Pro Rev B. (Core 2 Duo and Atheros AR5008).

I tried ndiswrapper and madwifi.

- ndiswrapper (1.38 from Synaptic or 1.42 from a self compiled) makes the Mac unbootable with the following message "Soft lockup on CPU#0"). I tested my previous driver used with Edgy (from DLink) and another one from [http://minipci.biz/support.html]("http://minipci.biz/support.html").

- The madwifi driver (I compiled and tested the 0.9.30.10) works when just installed but also makes the Mac unbootable.

So let's publish here our problems and, if possible, our tips to improve this bad situation.

---

### Post by ronocdh on 2007-05-01
Sucks about your lock up problems. But as Azaroth pointed out yesterday, the 1.43 build of ndiswrapper (released just yesterday!) is purported to resolve a lot of issues with the Atheros chipsets. I would compile 1.43 from source and give that a go.

---

### Post by Romu on 2007-05-01
So here a possible fix fr the madwifi issue :
[http://ubuntuforums.org/showthread.php?p=2572828&posted=1#post2572828]("http://ubuntuforums.org/showthread.php?p=2572828&posted=1#post2572828")

But I wonder if my problem with madwifi didn't come from "sudo modprobe wlan_scan_sta" as the Widemos' doesn't call it.

---

