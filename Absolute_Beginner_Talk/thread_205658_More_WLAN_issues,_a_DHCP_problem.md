---
title: "More WLAN issues, a DHCP problem?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Handssolow on 2006-06-28
After many hours I'm still having problems getting onto the internet with Kubuntu 6.06 . Like all things with computers, it's simple when you know how, otherwise its exxtreemly frustrating.

My belkin ralink 2500 PCI card is recognised as ra0.
I've looked at
sudo nano /etc/network/interfaces
I noticed that my ESSID, WEP key were correct but I added a line to set my correct wireless channel. Now when I boot I should not need to configure the channel.

Question 1

Is there any problem caused by this Ralink 2500 network card being called ra0 and not wlan0? I noticed in the above interfaces file that wlan0 appears as well as ra0. No risk of any conflicts or missing bits of programming? 

To continue
sudo iwconfig 
now more consistently shows my correct wireless settings, the MAC of my access point (a Linksys WAG54G) and link quality of about 50/100.

sudo dhclient rao
reports no DHCP offers
no working leases in persistent database -sleeping

When I use my XP PC to look at my router's communications, I see that my Linux PC is recognised in the "Wireless Clients Connected" window, indeed I see the MAC addresses of my family's three PCs that are switched on. I see their three IP addresses 192.168.1.100    192.168.1.101 and 192 .168.1.102 

However when I look my router's "DHCP Clients Table", only my two XP PCs are listed, not the PC running Kubuntu.

Earlier today I was briefly able to access Google on my linux PC, to only lose the internet when I tried move to this web site. Equally rarely am I able to access my router with the Konqueror web browser.

Question 2

What do I need to do to configure my Kubuntu os to access the internet?****

---

### Post by dmizer on 2006-06-28
[QUOTE=Handssolow]sudo dhclient rao
reports no DHCP offers
no working leases in persistent database -sleeping[/QUOTE]
did you actually type rao, or ra0 as in ra<zero>?  or was that just a typo?

have you disabled ipv6 yet? [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

