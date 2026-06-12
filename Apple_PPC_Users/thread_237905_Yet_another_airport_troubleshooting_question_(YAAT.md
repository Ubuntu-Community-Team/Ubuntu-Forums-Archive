---
title: "Yet another airport troubleshooting question (YAATQ)"
date: 2006-08-16
forum: Apple PPC Users
---

### Post by SWedd on 2006-08-16
Hi,

I hope this is not a common and tiresome query. I have searched as many forums and wikis as I could find for an answer but without joy. Whenever I see a post that describes something similar to the problem I am experiencing it has gone unanswered.

I'm having problems getting my wireless connection working on Ubuntu on my G4 Powerbook.

Note that the problem described below occurs whether my network is using WPA, WAP, or no encryption at all.

I've extracted the firmware from the OSX driver (also tried using wl_apsta.o with similar results) without any problems. The Ubuntu Network application then detects the local wireless networks but times out when attempting to join them.

I installed network manager (and commented out my wireless interface in /etc/network/interfaces) and it also detects my local networks. Attempting to join a network using network manager results in one of the two "lights" in the icon turning green, and then timing out while attempting to obtain an IP address.

I have also tried various scripts I have seen suggested on the internet, but the result always seems the same: When the script gets to "sudo dhclient", the attempts to aquire an IP address via DHCP time out repeatedly and it eventually gives up.

So yeah, DHCP seems to be the problem but I don't know why.

For completeness, I can connect to wireless networks from OS X (using DHCP) without any issues.

If anyone out there has had a similar problem and/or found a solution, that would be extremely helpful.

---

### Post by wallison on 2006-08-17
Didn't want you to feel alone, I'm having the same problem. It seems that I can scan and see wireless networks (my own and a neighbors), but not connect.
I too have used the AppleAirPort2 and wl_apsta.o firmware with the same results. I also tried to configure eth1 with a static IP.  Running out of ideas.

---

### Post by SWedd on 2006-08-17
Thanks for the moral support :)
Will let you know if I happen to get it to work while tinkering...

---

### Post by OlaNordmann on 2006-08-17
Exact same problem here. Connecting via the pre-installed Networking Administation tool works fine. However I can't connect to the found Access Points in Network Manager. :(

---

### Post by SWedd on 2006-08-17
> **OlaNordmann said:**
> Exact same problem here. Connecting via the pre-installed Networking Administation tool works fine. However I can't connect to the found Access Points in Network Manager. :(

Interesting, you say you can connect via the Network Administration tool? I can't seem to connect in any way.

Maybe it's not quite the same problem ... could you tell me the exact steps you use to do this?

(Edit: Did you comment out the wireless interfaces in /etc/network/interfaces before using network manager?)

---

### Post by OlaNordmann on 2006-08-17
> Interesting, you say you can connect via the Network Administration tool? I can't seem to connect in any way. could you tell me the exact steps you use to do this?
Sorry, I must not have read your post too carefully, and assumed i was in the same situation. I'm using Linksys WPC54G v3 (Broadcom Corporation BCM4318 802.11/g Wireless LAN chipset) which is only supported by Windows. But with alittle help from NdisWrapper (a utility that implements Windows kernel API and NDIS API within Linux kernel) I as able to get it working after alot of hassle. But fact being that your card has an OS X driver/firmware, i'm afraid this won't help you any further.


> Did you comment out the wireless interfaces in /etc/network/interfaces before using network manager?
There are no comments in */etc/network/interfaces*. Any other tips?
I think it's weird that Network Manager won't connect to the access points it has discovered, even though there's no restrictions on them. But the Networking Administation Tool, has no problems. Further more, I'd like to use the Network Manager instead; It's simple, it discovers Access Points automaticly, and supports WPA2-Personal Encryption.

---

### Post by SWedd on 2006-08-18
> **OlaNordmann said:**
> There are no comments in */etc/network/interfaces*. Any other tips?

From the HOWTOs I have read related to wifi and network manager, I think you have to comment-out (ie. remove) any wireless interfaces in the /etc/network/interfaces file yourself in order to get network manager to work.

Worth a try, anyway.

---

### Post by OlaNordmann on 2006-08-18
Thank you, that worked fantastic!

---

### Post by closet geek on 2006-08-18
SWedd,

What type of network are you trying to connect to? Is it an Ad-Hoc network? I couldn't connect to Ad-Hoc networks with my PB G4 but I could connect to a Router as long as the signal wasn't too weak.

Are you sure you are bringing the interface up in the correct order as listed in the howto's?

What sort of outputs are you getting in dmesg?

cg

---

### Post by SWedd on 2006-08-19
> **closet geek said:**
> SWedd,

What type of network are you trying to connect to? Is it an Ad-Hoc network? I couldn't connect to Ad-Hoc networks with my PB G4 but I could connect to a Router as long as the signal wasn't too weak.

I've got it set to a Managed network at the moment which from what I can tell is the normal case for connecting to the internet via airport? If it should be something else then please let me know...

Interestingly, I noticed earlier that if I set my network to no encryption at all I can actually connect! But not when using either WPA or WEP. (Previously I had only attempted to connect to my neighbours 'free' network, without success)

> **closet geek said:**
> Are you sure you are bringing the interface up in the correct order as listed in the howto's?

Not exactly sure what you're referring to here, it might be something I've missed. The wireless interface is the only one I am using at the moment.

> **closet geek said:**
> What sort of outputs are you getting in dmesg?

Just checked dmesg and it is as follows:

```
[  375.010533] printk: 4 messages suppressed.
[  375.010546] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  375.362835] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  375.719814] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  376.103746] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  376.487752] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  377.855738] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  378.243712] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  378.635730] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  380.003729] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  380.391753] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  381.751732] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  382.139728] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  386.023726] printk: 4 messages suppressed.
[  386.023739] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  386.226826] eth1: no IPv6 routers present
[  390.311741] printk: 5 messages suppressed.
[  390.311755] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  395.935728] printk: 6 messages suppressed.
[  395.935740] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  400.215725] printk: 5 messages suppressed.
[  400.215739] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  405.719868] printk: 3 messages suppressed.
[  405.719880] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  410.987730] printk: 5 messages suppressed.
[  410.987742] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  415.291728] printk: 5 messages suppressed.
[  415.291742] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  420.955735] printk: 6 messages suppressed.
[  420.955749] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  426.087746] printk: 2 messages suppressed.
[  426.087761] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  430.375731] printk: 5 messages suppressed.
[  430.375744] SoftMAC: Open Authentication completed with 00:11:24:5d:41:83
[  459.902824] eth1: no IPv6 routers present

```

Any ideas?

---

### Post by closet geek on 2006-08-19
Well if you can connect without WEP/WPA that's a good sign. You should have no problems connecting to WEP out of the box, WPA is a bit trickier. You should take a look through some of the howto's on this as they give guidance on getting WPA to work.

cg

---

### Post by SWedd on 2006-08-19
Alright, I got it working!

My previous assumption that non-encrypted links were not working proved to be my downfall I think. After I started focusing on the WPA side I discovered that I had been entering my passphrase incorrectly.

Under OSX entering a simple, short ASCII password is sufficient, and I thought (perhaps naively) that I could use the same password in Network Manager but it turns out I was wrong.

Anyway, I got the real password using 'wpa_passphrase <ssid> <passphrase>' from the command prompt. Then entering that into Network Manager when prompted worked.

So if anyone out there is also laboring under the misconception that they can use their OS X passphrase as their Network Manager password, hopefully this will help.

---

### Post by GurgieTrueshot on 2006-11-20
I am experiencing the same issues as everyone else. I can get it working through the Network Manager if it is on an unprotected network, however WPA and WEP won't work. I can't get a DHCP lease like someone stated above. However, if the WPA mechanism is failing it would make sense that the AP wouldn't hand out lease. I have tried various things including firmware installs and so forth. It is rather frustrating though. I may be in small town Kansas but I wmy access point secure.

I am currently downloading 6.10 I am hoping that there might be some fixes in that or that it just might work miraculously. I will keep you updated.

Edit:
I guess I should have read a little further before I posted

---

